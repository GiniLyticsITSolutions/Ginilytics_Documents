# SmartClinic Document Intelligence
## Complete Guide — What It Is, How It Works, and Who It Helps

---

## 1. What Is Document Intelligence?

SmartClinic Document Intelligence is an AI-powered system that lets patients, doctors, and hospital staff **upload any medical document and then have a real conversation with it**.

Instead of manually reading through pages of lab reports, insurance EOBs, discharge summaries, and hospital bills, users simply ask questions in plain English and get instant, grounded answers — with citations pointing back to the exact source text.

> **Example:** A patient uploads their discharge summary and asks *"What medications do I need to take and for how long?"* — the AI reads the document and answers precisely, with the matched passage highlighted as proof.

---

## 2. The Problem It Solves

### For Patients
- Medical documents are long, jargon-heavy, and overwhelming
- Patients don't know what their insurance paid vs. what they owe
- Prescription instructions get lost or misunderstood after discharge
- Lab reports contain critical abnormal values that go unnoticed

### For Hospitals & Clinics
- Staff spend hours manually reviewing documents for verification
- Insurance claims require cross-referencing multiple documents
- Billing errors happen when financial data is extracted manually
- Compliance audits require fast document retrieval and traceability

### For Doctors
- Reviewing a patient's uploaded records before an appointment takes time
- Referral letters and prior lab results are scattered across systems
- Prescription history and dosage details are hard to quickly surface

---

## 3. How It Works — End to End

```
┌─────────────────────────────────────────────────────────────────────┐
│                     DOCUMENT INTELLIGENCE PIPELINE                  │
└─────────────────────────────────────────────────────────────────────┘

  1. UPLOAD          2. OCR              3. AI EXTRACTION      4. INDEXING
  ──────────         ──────────          ────────────────      ──────────
  Patient/Staff  →   Tesseract reads →   Qwen LLM classifies   Text is split
  uploads PDF,       every page and      document type and      into overlapping
  JPG, or PNG        extracts raw text   pulls structured       800-char chunks
  via the portal                         fields (patient        stored in DB
                                         name, diagnosis,       for fast search
                                         amounts, dates, etc.)

  5. CHAT             6. RETRIEVAL         7. AI ANSWER         8. CITATION
  ──────────          ─────────────        ────────────         ──────────
  User asks a    →    BM25 scoring    →    Qwen LLM reads   →   Answer returned
  question in         finds the top-5      the matched          with source
  plain English       most relevant        chunks and           document title,
                      chunks from          generates a          snippet, and
                      their documents      grounded answer      confidence score
```

### Key Technical Components

| Component | Technology | Purpose |
|-----------|-----------|---------|
| OCR Engine | Tesseract + Poppler | Reads PDF/image text |
| AI Model | Qwen2.5-Coder-7B via vLLM | Extraction + chat answers |
| Search | BM25 relevance scoring | Finds relevant text chunks |
| Storage | PostgreSQL + local filesystem | Documents + embeddings |
| API | Go / Gin | REST endpoints |
| Frontend | Next.js + TypeScript | Patient & staff UI |

---

## 4. Supported Document Types

| Type | What It Extracts | Chat Can Answer |
|------|-----------------|-----------------|
| **Lab Report** | Test names, results, abnormal flags, reference ranges | "What values are abnormal?", "Is my cholesterol high?" |
| **Discharge Summary** | Diagnosis, procedure, medications, follow-up dates | "How long was I admitted?", "What are my restrictions?" |
| **Prescription** | Drug name, dosage, frequency, refills, warnings | "What are my medications?", "Can I refill Oxycodone?" |
| **Hospital Bill** | Line items, total charges, insurance paid, patient balance | "How much do I owe?", "What did insurance cover?" |
| **Insurance EOB** | Claim number, allowed amount, plan paid, deductible | "Was my claim approved?", "What is my remaining deductible?" |
| **Insurance Card** | Policy number, group, insurer name | "What is my policy number?", "Who is my insurer?" |
| **Radiology Report** | Diagnosis codes, findings, physician | "What did my MRI show?" |
| **Referral Letter** | Referring doctor, reason, specialist | "Why was I referred?" |

---

## 5. Who Uses It and How

### Patient Portal
Patients log in and can:
- Upload their own medical records from any provider
- Ask the AI about their medications, diagnoses, and bills
- See exactly which part of which document the answer came from
- View AI-generated summaries of each document
- Track their insurance coverage and out-of-pocket costs

**Example session:**
```
Patient: "What medications was I discharged with and are there any warnings?"

AI: Based on your prescription (prescription_emily_rodriguez.txt):
You were prescribed 4 medications:
• Apixaban 2.5mg (Eliquis) — twice daily for 35 days for blood clot prevention
• Oxycodone/Acetaminophen 5/325mg — every 6 hours as needed for pain (controlled substance, 0 refills)
• Pantoprazole 40mg — once daily before breakfast
• Aspirin 81mg — once daily

⚠️ Warning: Do not drive or operate heavy machinery while taking Oxycodone.
Do not take other acetaminophen products alongside Percocet.

Source: prescription_emily_rodriguez.txt — "Controlled substance — no early refills.
Do not drive or operate heavy machinery."

This answer is based only on your accessible uploaded/shared documents and should
be reviewed by medical staff.
```

---

### Doctor Portal
Doctors can:
- View documents uploaded by their assigned patients
- Ask clinical questions before appointments
- Get instant summaries of referral letters and lab histories
- Verify prescription details without hunting through records

**Example session:**
```
Doctor: "What abnormal lab results does James Anderson have that I should review?"

AI: Based on lab_report_james_anderson.txt (dated May 19, 2026):

4 abnormal values flagged:
• HbA1c: 5.9% — HIGH (pre-diabetic range, normal < 5.7%)
• LDL Cholesterol: 142 mg/dL — HIGH (normal < 100 mg/dL)
• Total Cholesterol: 218 mg/dL — HIGH (normal < 200 mg/dL)
• Triglycerides: 170 mg/dL — HIGH (normal < 150 mg/dL)
• Fasting Glucose: 108 mg/dL — HIGH (normal 70-100 mg/dL)

The lab report recommends dietary counseling and consideration of statin therapy.
Follow-up in 4-6 weeks advised.
```

---

### Hospital Admin / Billing Staff
Admins can:
- Monitor all documents uploaded across the hospital
- Track claim status across multiple patients
- Use AI to cross-check bill totals against EOBs
- Quickly surface any outstanding patient balances
- Run the document extraction workflow for bulk processing

**Example session:**
```
Admin: "Show me all insurance claims and how much each patient owes"

AI: Based on your hospital documents:

Patient          | Insurer | Claim #              | Total Bill  | Insurer Paid | Patient Owes
Emily Rodriguez  | BCBS    | BCBS-CLM-2026-44782  | $48,750     | $28,460      | $4,470
Robert Thompson  | Aetna   | AET-2026-98321       | $59,835     | $36,934      | $8,373

Combined outstanding patient receivables: $12,843.64
```

---

## 6. Setup & Configuration

### Prerequisites
- Go 1.21+
- PostgreSQL 15+
- Tesseract OCR (for PDF/image processing)
- Poppler utilities (`pdftoppm` for PDF to image conversion)
- A running vLLM server (or Claude API key)

### Environment Variables

Create `apps/api/.env`:

```env
# Database
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=Admin@123
DB_NAME=smartclinic

# App
PORT=8080
JWT_SECRET=your-jwt-secret

# AI — vLLM (self-hosted)
AI_ENABLED=true
AI_PROVIDER=vllm
AI_API_BASE_URL=https://your-vllm-server.ngrok-free.dev/vllm/v1
AI_MODEL=Qwen/Qwen2.5-Coder-7B-Instruct
AI_API_KEY=your-vllm-secret-key
AI_TIMEOUT_SECONDS=120
AI_MAX_TOKENS=2048
AI_TEMPERATURE=0.1

# Alternatively — Claude API (Anthropic)
# AI_PROVIDER=claude
# AI_API_KEY=sk-ant-api03-...
# AI_MODEL=claude-haiku-4-5-20251001

# Document Storage
DOCUMENT_LOCAL_UPLOAD_PATH=./uploads/documents
DOCUMENT_MAX_FILE_SIZE_MB=20
OCR_PROVIDER=tesseract
TESSERACT_PATH=tesseract
TESSERACT_LANG=eng
```

### Installing OCR Dependencies

**Windows:**
```bash
# Tesseract — download from https://github.com/UB-Mannheim/tesseract/wiki
# Add to PATH: C:\Program Files\Tesseract-OCR\

# Poppler — download from https://github.com/oschwartz10612/poppler-windows
# Add to PATH: C:\poppler\Library\bin\
```

**Linux / Ubuntu:**
```bash
sudo apt-get install tesseract-ocr poppler-utils
```

**macOS:**
```bash
brew install tesseract poppler
```

---

## 7. API Endpoints

### Document Lifecycle

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/documents/upload` | Upload a document file |
| `GET` | `/documents` | List all documents for a hospital/user |
| `GET` | `/documents/:id` | Get a specific document |
| `POST` | `/documents/:id/extract` | Run OCR + AI extraction on a document |
| `GET` | `/documents/:id/ocr` | Get the raw OCR text of a document |
| `GET` | `/documents/:id/summary` | Get the AI-generated summary |
| `POST` | `/documents/:id/generate-summary` | Generate a new AI summary |
| `POST` | `/documents/:id/verify` | Mark extraction as verified |
| `POST` | `/documents/:id/reject` | Reject extraction for re-review |

### Document Chat

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/documents/chat` | Ask a question about uploaded documents |

**Chat request body:**
```json
{
  "query": "What medications was I prescribed?",
  "hospital_id": "uuid",
  "user_id": "uuid",
  "session_id": "uuid (optional — omit to start new conversation)"
}
```

**Chat response:**
```json
{
  "answer": "You were prescribed 4 medications...",
  "confidence_score": 0.96,
  "session_id": "uuid (send this back for follow-up questions)",
  "sources": [
    {
      "document_id": "uuid",
      "document_title": "prescription_emily_rodriguez.txt",
      "document_type": "prescription",
      "snippet": "Rx #1: APIXABAN (ELIQUIS) 2.5 mg tablets...",
      "confidence": 0.96,
      "page_number": null,
      "file_url": "/uploads/documents/..."
    }
  ],
  "disclaimer": "This answer is based only on your accessible uploaded/shared documents and should be reviewed by medical staff."
}
```

---

## 8. Document Processing Workflow

### After a document is uploaded:

```
1. POST /documents/upload
   → DocumentUpload record created (status: "uploaded")

2. POST /documents/:id/extract
   → Tesseract OCR runs on the file
   → Qwen LLM classifies document type and extracts fields
   → ExtractedDocument record created (status: "extracted")
   → Document chunked into 800-char overlapping segments
   → DocumentEmbedding records created (BM25 index built)

3. GET /documents/:id/summary  (optional)
   → AI generates a human-readable summary with highlights and next actions

4. POST /documents/:id/verify  (optional — for clinic workflows)
   → Staff reviews and verifies extraction accuracy
   → Status updated to "verified"

5. POST /documents/chat
   → User asks a question
   → BM25 scoring finds relevant chunks
   → Qwen LLM generates grounded answer
   → Chat session + messages stored for history
```

---

## 9. Confidence Scoring

Every document and answer carries confidence scores that reflect extraction quality:

| Score | Meaning |
|-------|---------|
| 0.95 – 1.00 | High confidence — clear, well-structured document |
| 0.80 – 0.94 | Good confidence — minor OCR noise or formatting issues |
| 0.60 – 0.79 | Moderate — document may need manual review |
| < 0.60 | Low — poor scan quality or unsupported format |

The chat UI displays confidence as a percentage badge on each source citation.

---

## 10. Multi-Turn Conversation (Sessions)

The chat system maintains conversation history through `session_id`:

```
Turn 1: "What was Emily's diagnosis?"
        → session_id: "abc-123" returned

Turn 2: "And what did BCBS pay for that?"
        → Send session_id: "abc-123"
        → AI has context from Turn 1 and connects the answers

Turn 3: "Is there any outstanding balance?"
        → Same session — AI can reference all prior turns
```

Each session is stored in `DocumentChatSession` and `DocumentChatMessage` tables, enabling full conversation audit trails for HIPAA compliance.

---

## 11. Security & HIPAA Compliance

| Measure | Implementation |
|---------|---------------|
| Path traversal prevention | File storage validates all paths before write |
| Role-based document access | Documents scoped to hospital + user |
| Complete audit trail | Every upload, extraction, view, and chat stored in `DocumentAuditLog` |
| Multi-tenancy | All queries scoped to `hospital_id` — data never crosses tenant boundaries |
| No external data transmission | All documents stay on your infrastructure; only anonymized text chunks sent to the LLM |
| File type whitelist | Only PDF, JPG, PNG, WebP accepted |
| Controlled substance logging | Prescription chat answers include disclaimer |

---

## 12. Demo Credentials & Test Data

The following documents are pre-loaded for `hospadmin@ginilytics.com` at SmartCare Multispeciality Hospital:

| Document | Patient | Highlights |
|----------|---------|-----------|
| `lab_report_james_anderson.txt` | James Anderson | Pre-diabetes, high LDL, dyslipidemia |
| `discharge_summary_emily_rodriguez.txt` | Emily Rodriguez | Hip replacement, 5-day stay, $48,750 bill, BCBS paid $28,460 |
| `prescription_emily_rodriguez.txt` | Emily Rodriguez | 4 medications incl. Apixaban + controlled substance |
| `eob_bcbs_emily_rodriguez.txt` | Emily Rodriguez | BCBS paid $32,786, patient owes $3,058 |
| `hospital_bill_robert_thompson.txt` | Robert Thompson | Heart stent (PCI), $59,835 total, Aetna paid $36,934 |

### Best Demo Questions

```
"What abnormal lab results does James Anderson have?"
"What medications was Emily prescribed and are there any warnings?"
"How much did BCBS pay for the hip surgery and what does the patient still owe?"
"What was the heart procedure performed on Robert Thompson?"
"Show me all insurance claims with amounts paid and patient balances"
"What are the discharge instructions after the hip replacement?"
"Which patients have high cholesterol based on their lab reports?"
"What is the total outstanding patient balance across all documents?"
```

---

## 13. Roadmap — What's Next

| Feature | Status | Priority |
|---------|--------|----------|
| OCR + AI Extraction | ✅ Complete | — |
| Document Chat (BM25 RAG) | ✅ Complete | — |
| Session persistence (multi-turn) | ✅ Complete | — |
| Claude API support | ✅ Complete | — |
| vLLM support (Qwen, LLaMA) | ✅ Complete | — |
| Document summaries | ✅ Complete | — |
| Confidence scoring | ✅ Complete | — |
| Verification workflow | ✅ Complete | — |
| Vector embeddings (semantic search) | 🔲 Planned | High |
| Document sharing between users | 🔲 Planned | High |
| Bulk document upload | 🔲 Planned | Medium |
| S3 / cloud storage | 🔲 Planned | Medium |
| Insurance claim auto-filing | 🔲 Planned | High |
| Mobile app (React Native) | 🔲 Planned | Medium |

---

## 14. Frequently Asked Questions

**Q: Does the AI make up information?**
No. The system is grounded — it only answers from the text in your uploaded documents. If the information is not in the document, it says so explicitly.

**Q: What happens if OCR quality is poor?**
The confidence score drops below 0.80 and the document is flagged for manual review. Staff can verify or reject the extraction.

**Q: Can multiple patients use the same system?**
Yes. All data is fully multi-tenant — each hospital and patient only ever sees their own documents. There is no data leakage between users.

**Q: Does the AI send patient data to the cloud?**
Only if you use a cloud-based AI provider (Claude API). If you use a self-hosted vLLM server, all data stays on-premise. The system is designed for both modes.

**Q: How long does extraction take?**
OCR typically takes 2–10 seconds per page. AI extraction adds 3–8 seconds via the LLM. Total time for a typical 2-page PDF is under 20 seconds.

**Q: What file formats are supported?**
PDF, JPG, JPEG, PNG, and WebP. Maximum file size is 20 MB (configurable).

---

*Documentation version: 1.0 | Last updated: May 2026 | SmartClinic Document Intelligence*
