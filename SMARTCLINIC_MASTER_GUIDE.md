# SmartClinic — Complete Product Guide
## What It Is, Who It Helps, and How to Run It

---

## Table of Contents

1. [What Is SmartClinic?](#1-what-is-smartclinic)
2. [Who It Helps — By Role](#2-who-it-helps--by-role)
3. [Full Feature Catalog](#3-full-feature-catalog)
4. [System Architecture](#4-system-architecture)
5. [Getting Started — Local Setup](#5-getting-started--local-setup)
6. [Demo Credentials](#6-demo-credentials)
7. [Module Reference](#7-module-reference)
8. [AI & Document Intelligence](#8-ai--document-intelligence)
9. [Deployment](#9-deployment)
10. [Roadmap & What's Next](#10-roadmap--whats-next)

---

## 1. What Is SmartClinic?

SmartClinic is a **full-stack hospital management platform** built for modern healthcare providers. It replaces paper-based workflows, disconnected billing software, and manual document review with a single integrated system that every stakeholder — patient, doctor, nurse, pharmacist, billing staff, and administrator — can use from a single login.

At its core, SmartClinic solves three fundamental problems in healthcare:

**1. Information is scattered.** Patient records, lab results, discharge summaries, prescriptions, and insurance documents live in separate systems or on paper. SmartClinic puts everything in one place with AI that can read and explain any document.

**2. Workflows are manual and slow.** Appointment booking, insurance pre-authorization, claim filing, IPD admission, pharmacy dispensing, and billing all require staff to hand-carry information between departments. SmartClinic automates these handoffs.

**3. Billing leaks money.** Missed charge captures, delayed claim submissions, denied claims that go un-appealed, and billing errors cost hospitals 5–15% of revenue. SmartClinic tracks every billable event and flags anomalies in real time.

---

## 2. Who It Helps — By Role

### Patient
A patient logs into their portal and can see everything about their own care — without calling the hospital.

**What they can do:**
- Book appointments online and see upcoming and past visits
- Upload their own medical documents (from any provider) and ask the AI questions about them
- View lab results with AI explanations of abnormal values
- See exactly what their insurer paid vs. what they owe — line by line
- Check insurance pre-authorization status before a procedure
- Chat with their doctor in real time (secure, HIPAA-compliant)
- Join a video consultation from their browser
- View their full medical timeline across visits, IPD stays, and procedures
- Get AI-generated summaries of their discharge instructions in plain English

**Example moment of value:**
> A patient is discharged after hip replacement surgery. Instead of trying to read a 6-page discharge summary, they open SmartClinic, upload the summary, and ask: *"What medications do I take and for how long?"* The AI reads the document and answers with the exact drugs, dosages, and warnings — pulled directly from the text.

---

### Doctor
Doctors spend most of their time on information retrieval — reading past notes, reviewing labs, checking prescriptions. SmartClinic gives doctors instant context for every patient they see.

**What they can do:**
- See their full appointment schedule for the day, week, or month
- Access patient medical history, past diagnoses, lab results, and prescriptions in one view
- Review documents uploaded by their patients before appointments
- Ask AI questions about a patient's records: *"What abnormal labs does this patient have?"*
- Issue digital prescriptions linked directly to the patient record
- Order lab tests and receive results automatically in the patient's chart
- Write consultation notes with structured templates
- Refer patients to specialists with auto-generated referral letters
- Conduct video consultations via Jitsi (no app download required)
- Chat securely with patients between appointments
- Set their availability and block personal time

**Example moment of value:**
> A doctor is seeing a new patient who transferred from another hospital. In 30 seconds they ask SmartClinic: *"What is this patient's prescription history and are there any drug interactions to watch?"* The AI reads the uploaded records and highlights relevant data — so the doctor walks in prepared instead of starting from scratch.

---

### Hospital Administrator
Hospital admins need visibility across all departments simultaneously — staffing, occupancy, revenue, compliance, and claims.

**What they can do:**
- View real-time occupancy across all wards, ICU, and OT
- Register new doctors and staff and assign their roles and permissions
- Monitor all active insurance claims and their status (submitted, approved, denied)
- See the full billing pipeline — what's been invoiced, what's been paid, what's outstanding
- Track IPD admissions and discharges
- Manage employee payroll, HR records, and clock-in/clock-out
- View AI-generated revenue forecasts for the next 30/60/90 days
- Monitor document extraction quality and verify AI-extracted data
- Set hospital-level settings, specialties, and service configurations
- Track compliance risks and audit readiness scores

**Example moment of value:**
> The billing manager asks SmartClinic: *"Show me all insurance claims and how much each patient still owes."* In seconds they get a table with every claim, insurer, amount paid, and outstanding patient balance — without opening a single spreadsheet.

---

### Reception Staff
Reception is the front door of every hospital. SmartClinic makes check-in fast, queue management visible, and handoff to billing seamless.

**What they can do:**
- Check in walk-in and pre-booked patients in under 60 seconds
- View and manage the real-time patient queue by department
- Collect patient demographic and insurance information at arrival
- Assign patients to available doctors based on specialty and wait time
- Hand off completed visits to billing with one click
- Manage room assignments

---

### Pharmacy Staff
The pharmacy module connects prescriptions issued by doctors directly to dispensing — eliminating the paper prescription entirely.

**What they can do:**
- See all pending prescriptions in real time as doctors issue them
- Dispense medications and mark prescriptions as fulfilled
- Manage drug inventory with low-stock alerts
- Record stock received from suppliers (Cardinal Health, McKesson, etc.)
- Generate dispensing reports and consumption analytics
- Track controlled substance dispensing with full audit trails

---

### Lab Staff
Lab orders flow directly from the doctor's prescription pad to the lab queue.

**What they can do:**
- See all pending lab test orders by doctor and patient
- Record test results and mark orders as complete
- Upload result documents (PDFs, images) that attach to the patient record
- Results automatically appear in the patient's portal and notify the doctor

---

### Billing Staff
SmartClinic tracks every billable event automatically so nothing falls through the cracks.

**What they can do:**
- Generate itemized invoices from IPD stays, OPD visits, procedures, lab tests, and pharmacy dispensing
- Submit insurance claims electronically
- Track claim status (submitted → under review → approved/denied)
- Manage claim appeals when denied
- View the CFO dashboard: clean claim rate, recoverable gaps, contract risks
- Process patient payments and track outstanding balances

---

### Nurse / Ward Staff
Nurses manage the moment-to-moment care of admitted patients (IPD).

**What they can do:**
- View all patients in their assigned ward
- Record vital signs, nursing notes, and medication administration
- Process patient admissions and prepare discharge documentation
- Transfer patients between wards or to other hospitals
- View the ward status board in real time

---

### Super Admin (Platform Level)
For the team operating SmartClinic as a SaaS product for multiple hospitals.

**What they can do:**
- Manage all hospitals on the platform
- Monitor AI usage and document processing across all tenants
- Manage subscription plans and billing for hospital clients
- View cross-hospital analytics
- Oversee platform-wide compliance

---

## 3. Full Feature Catalog

### Clinical Operations
| Feature | Description | Status |
|---------|-------------|--------|
| Appointment booking | Patients book online; doctors see schedule with availability rules | ✅ Live |
| OPD workflow | Walk-in queue management, check-in, consultation notes | ✅ Live |
| IPD management | Admission, ward assignment, vitals, nursing notes, discharge | ✅ Live |
| Patient transfers | Transfer between wards or hospitals with documentation | ✅ Live |
| Lab test ordering | Doctor orders → lab queue → result upload → patient record | ✅ Live |
| Prescription management | Digital prescriptions linked to patient record | ✅ Live |
| Video consultation | Browser-based video via Jitsi — no app download | ✅ Live |
| Doctor–patient chat | Secure real-time messaging (WebSocket) | ✅ Live |
| EMR | Electronic medical records with medical history timeline | ✅ Live |
| Doctor templates | Reusable consultation and prescription templates | ✅ Live |
| Patient reviews | Post-visit rating and feedback for doctors | ✅ Live |

### Document Intelligence (AI-Powered)
| Feature | Description | Status |
|---------|-------------|--------|
| Document upload | PDF, JPG, PNG, WebP — up to 20 MB | ✅ Live |
| OCR extraction | Tesseract reads every page of any scanned document | ✅ Live |
| AI classification | Identifies document type (lab report, bill, prescription, EOB, etc.) | ✅ Live |
| Structured field extraction | Pulls patient name, amounts, diagnosis, medications, dates | ✅ Live |
| Document chat | Ask any question in plain English, get a cited answer | ✅ Live |
| Multi-turn conversations | Follow-up questions maintain context across turns | ✅ Live |
| AI document summaries | One-paragraph plain-English summary of any document | ✅ Live |
| Confidence scoring | Every answer carries a quality score (0–1) | ✅ Live |
| Verification workflow | Staff can verify or reject AI extractions | ✅ Live |
| Audit trail | Every upload, extraction, view, and chat logged for HIPAA | ✅ Live |
| Session history | Full chat history stored per user | ✅ Live |
| Semantic search | Vector embeddings for similarity-based retrieval | 🔲 Planned |
| Document sharing | Share a document with specific doctors | 🔲 Planned |
| S3 / cloud storage | Store documents in AWS S3 or Azure Blob | 🔲 Planned |

### Billing & Insurance
| Feature | Description | Status |
|---------|-------------|--------|
| Invoice generation | Auto-built from visit charges, IPD daily rates, procedures | ✅ Live |
| Insurance claim tracking | Submit and track claims by patient and insurer | ✅ Live |
| EOB parsing | AI reads Explanation of Benefits and extracts amounts | ✅ Live |
| Pre-authorization | Track pre-auth status and eligibility before procedures | ✅ Live |
| Denial management | Track denied claims, reasons, and recovery pipeline | ✅ Live |
| CFO dashboard | Clean claim rate, revenue gaps, contract risk overview | ✅ Live |
| Revenue forecasting | AI-based 30/60/90-day revenue projections | ✅ Live |
| Insurance auto-filing | Direct electronic submission to payers | 🔲 Planned |
| Payment gateway | Patient payments via Stripe | ✅ Live |

### Hospital Operations
| Feature | Description | Status |
|---------|-------------|--------|
| Multi-hospital support | Full multi-tenancy — each hospital's data is isolated | ✅ Live |
| Role-based access | 10+ roles with granular permissions per feature | ✅ Live |
| Staff management | Doctor and employee onboarding, profiles, schedules | ✅ Live |
| HR & payroll | Clock-in/out, leave tracking, salary records | ✅ Live |
| Pharmacy inventory | Drug stock, suppliers, low-stock alerts, dispensing | ✅ Live |
| Queue management | Real-time patient queue display by department | ✅ Live |
| Analytics | Occupancy, revenue, patient volume by department | ✅ Live |
| Bulk data import | Migrate patient records in bulk from legacy systems | ✅ Live |
| Notifications | In-app and email alerts for appointments, results, claims | ✅ Live |
| Compliance tracking | Audit readiness score, open gaps, policy adherence | ✅ Live |
| Subscriptions | Hospital subscription plans (SaaS billing) | ✅ Live |

---

## 4. System Architecture

```
┌──────────────────────────────────────────────────────────────────────┐
│                        SmartClinic Platform                          │
├─────────────────────────────┬────────────────────────────────────────┤
│  Frontend (Next.js 16)      │  Backend (Go / Gin)                    │
│  apps/web                   │  apps/api                              │
│                             │                                        │
│  • Patient Portal           │  • REST API (36 modules)               │
│  • Doctor Dashboard         │  • JWT Authentication                  │
│  • Hospital Admin Panel     │  • Role-Based Permissions              │
│  • Reception & Queue        │  • WebSocket (real-time)               │
│  • Pharmacy & Lab           │  • Async Job Queue (Asynq)             │
│  • Document Chat UI         │  • AI / vLLM integration               │
│  • Billing & Claims         │  • Prometheus metrics                  │
└─────────────────────────────┼────────────────────────────────────────┘
                              │
         ┌────────────────────┼────────────────────┐
         ▼                    ▼                    ▼
   PostgreSQL 15+         Redis 7+           vLLM Server
   (primary store)    (cache / sessions)  (Qwen2.5-Coder-7B)
                                          or Anthropic Claude API
```

### Key Technology Choices

| Layer | Technology | Why |
|-------|-----------|-----|
| Backend | Go + Gin | Fast, statically typed, excellent concurrency |
| Database | PostgreSQL 15 + GORM | Relational integrity, JSONB for flexible fields |
| Frontend | Next.js 16 + React 19 | Server rendering, App Router, TypeScript |
| Auth | JWT + Redis blacklist | Stateless API auth with token revocation |
| AI (self-hosted) | vLLM + Qwen2.5-Coder-7B | On-premise, no patient data leaves your infrastructure |
| AI (cloud) | Claude API (Anthropic) | Highest-quality answers when on-premise isn't required |
| OCR | Tesseract + Poppler | Open-source, runs locally, handles PDF and images |
| Real-time | Gorilla WebSocket | Live chat, notifications, queue updates |
| Jobs | Asynq + Redis | Async processing for OCR, notifications, bulk import |
| Payments | Stripe | Industry standard, PCI-compliant |
| Video | Jitsi | Self-hostable, no per-minute fees |
| Monitoring | Prometheus + Grafana | Standard observability stack |

---

## 5. Getting Started — Local Setup

### Prerequisites

Install the following before starting:

| Dependency | Version | Install |
|-----------|---------|---------|
| Go | 1.21+ | https://go.dev/dl |
| Node.js | 20+ | https://nodejs.org |
| PostgreSQL | 15+ | https://www.postgresql.org/download |
| Tesseract OCR | 5.x | See below |
| Poppler | latest | See below |
| Redis | 7+ | https://redis.io/download (optional) |

**Install Tesseract + Poppler:**

Windows:
```
Tesseract: https://github.com/UB-Mannheim/tesseract/wiki
  → Install to C:\Program Files\Tesseract-OCR\
  → Add to PATH

Poppler: https://github.com/oschwartz10612/poppler-windows
  → Extract to C:\poppler\
  → Add C:\poppler\Library\bin\ to PATH
```

Linux/Ubuntu:
```bash
sudo apt-get install tesseract-ocr poppler-utils
```

macOS:
```bash
brew install tesseract poppler
```

---

### Step 1 — Clone and Configure

```bash
git clone https://github.com/your-org/smartclinic.git
cd smartclinic
```

Create the API environment file at `apps/api/.env`:

```env
# Database
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=your-postgres-password
DB_NAME=smartclinic

# App
PORT=8080
JWT_SECRET=your-secret-key-here
UPLOAD_DIR=./uploads

# Redis (set REDIS_ENABLED=false if not using Redis)
REDIS_ENABLED=false
REDIS_ADDR=localhost:6379
REDIS_PASSWORD=

# AI — choose one provider:

# Option A: Self-hosted vLLM (all data stays on-premise)
AI_ENABLED=true
AI_PROVIDER=vllm
AI_API_BASE_URL=https://your-vllm-server/vllm/v1
AI_MODEL=Qwen/Qwen2.5-Coder-7B-Instruct
AI_API_KEY=your-vllm-key
AI_TIMEOUT_SECONDS=120
AI_MAX_TOKENS=2048
AI_TEMPERATURE=0.1

# Option B: Claude API (Anthropic)
# AI_ENABLED=true
# AI_PROVIDER=claude
# AI_API_KEY=sk-ant-api03-...
# AI_MODEL=claude-haiku-4-5-20251001
# AI_TIMEOUT_SECONDS=30
# AI_MAX_TOKENS=1024

# Document Storage
DOCUMENT_STORAGE_PROVIDER=local
DOCUMENT_LOCAL_UPLOAD_PATH=./uploads/documents
DOCUMENT_MAX_FILE_SIZE_MB=20
OCR_PROVIDER=tesseract
OCR_ENABLED=true
TESSERACT_PATH=tesseract
TESSERACT_LANG=eng
```

---

### Step 2 — Start the Backend

```bash
cd apps/api

# Install dependencies
go mod download

# Create the database
psql -U postgres -c "CREATE DATABASE smartclinic;"

# Run the server (auto-migrates and seeds on first run)
go run ./cmd/server

# You should see:
# SmartClinic API running on :8080
```

The server auto-runs migrations and seeds demo data (users, hospital, patients, appointments) on first start.

---

### Step 3 — Start the Frontend

```bash
cd apps/web

# Install dependencies
npm install

# Start development server
npm run dev

# Open http://localhost:3000
```

---

### Step 4 — Seed Demo Documents (for Document Intelligence Demo)

```bash
cd apps/api

# Seeds 5 realistic medical documents for hospadmin@ginilytics.com
go run scratch/seed_demo_docs.go
```

This creates:
- James Anderson's lab report (pre-diabetes, high LDL)
- Emily Rodriguez's discharge summary (hip replacement, $48,750 bill)
- Emily Rodriguez's prescription (Apixaban, Oxycodone, Pantoprazole, Aspirin)
- BCBS Explanation of Benefits for Emily Rodriguez ($32,786 paid)
- Robert Thompson's hospital bill (heart stent, $59,835)

---

### Step 5 — Verify Everything Works

```bash
# Health check
curl http://localhost:8080/health

# Login
curl -X POST http://localhost:8080/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"hospadmin@ginilytics.com","password":"password123"}'
```

---

## 6. Demo Credentials

**Default password for all accounts: `password123`**

| Role | Email | Best For Showing |
|------|-------|-----------------|
| Super Admin | admin@ginilytics.com | Platform overview, subscription management |
| Hospital Admin | hospadmin@ginilytics.com | Document Intelligence, claims, analytics |
| Doctor | doctor@ginilytics.com | Appointment workflow, patient records, video |
| Patient | patient@ginilytics.com | Patient portal, AI document chat, billing |
| Lab Staff | lab@ginilytics.com | Lab order processing |
| Radiology Staff | radiology@ginilytics.com | Imaging workflow |
| Nurse | nurse@ginilytics.com | IPD ward management |
| Reception | reception@ginilytics.com | Check-in, queue, billing handoff |
| Pharmacy | pharmacy@ginilytics.com | Prescription dispensing, inventory |
| Billing | billing@ginilytics.com | Claims, invoices, CFO dashboard |

---

### Best Demo Flows for Prospects

**Flow 1 — Document AI (most impressive for first demos)**
1. Login as `hospadmin@ginilytics.com`
2. Go to Documents → Chat
3. Ask: *"What abnormal lab results does James Anderson have?"*
4. Ask: *"How much did BCBS pay for the hip surgery and what does Emily still owe?"*
5. Ask: *"Show me all insurance claims with amounts paid and patient balances"*
6. Ask: *"What medications was Emily prescribed and are there any warnings?"*

**Flow 2 — Patient Journey**
1. Login as `patient@ginilytics.com`
2. Show: upcoming appointments, medical history, lab results
3. Upload a PDF document → run extraction → ask AI questions about it
4. Show the insurance view: what was charged, what insurer paid, what patient owes

**Flow 3 — Hospital Operations**
1. Login as `hospadmin@ginilytics.com`
2. Show: analytics dashboard, IPD occupancy, queue
3. Show: claims monitor, revenue forecast
4. Show: HR → employee clock-in, payroll summary

**Flow 4 — Clinical Workflow**
1. Login as `doctor@ginilytics.com`
2. Show: today's appointment schedule
3. Click a patient → view lab results, past prescriptions
4. Issue a digital prescription
5. Start a video consultation (Jitsi)

---

## 7. Module Reference

### Backend Modules (apps/api/internal/modules/)

| Module | What It Does | Key Endpoints |
|--------|-------------|---------------|
| **auth** | Login, register, JWT refresh, logout | `/api/v1/auth/*` |
| **hospitals** | Hospital CRUD, settings, specialty config | `/api/v1/hospitals/*` |
| **doctors** | Doctor profiles, availability, schedules | `/api/v1/doctors/*` |
| **patients** | Patient registration, demographics, insurance | `/api/v1/patients/*` |
| **appointments** | Book, reschedule, cancel, complete appointments | `/api/v1/appointments/*` |
| **emr** | Consultation notes, medical history, diagnoses | `/api/v1/emr/*` |
| **ipd** | Admit, ward assign, vitals, discharge | `/api/v1/ipd/*` |
| **lab** | Order tests, upload results, view reports | `/api/v1/lab/*` |
| **prescriptions** | Issue, fulfill, view prescription history | `/api/v1/prescriptions/*` |
| **pharmacy** | Dispensing, inventory, suppliers, stock | `/api/v1/pharmacy/*` |
| **billing** | Invoices, payments, outstanding balances | `/api/v1/billing/*` |
| **insurance** | Claims, pre-auth, EOB, denial tracking | `/api/v1/insurance/*` |
| **documents** | Upload, OCR, AI extract, document chat | `/api/v1/documents/*` |
| **chat** | Real-time messaging between doctor and patient | `/api/v1/chat/*` |
| **video** | Jitsi room creation and access control | `/api/v1/video/*` |
| **notifications** | In-app alerts, email triggers | `/api/v1/notifications/*` |
| **reception** | Check-in, queue, room assignment | `/api/v1/reception/*` |
| **queue** | Patient queue state by department | `/api/v1/queue/*` |
| **hr** | Employee records, clock-in/out, leave | `/api/v1/hr/*` |
| **analytics** | Hospital KPIs, occupancy, revenue | `/api/v1/analytics/*` |
| **compliance** | HIPAA audit readiness, policy tracking | `/api/v1/compliance/*` |
| **audit** | Full audit log query and export | `/api/v1/audit/*` |
| **permissions** | Role and permission management | `/api/v1/permissions/*` |
| **subscriptions** | SaaS plan management | `/api/v1/subscriptions/*` |
| **admin** | Platform admin tools | `/api/v1/admin/*` |
| **saas_admin** | Multi-hospital oversight | `/api/v1/saas/*` |
| **transfers** | Inter-ward and inter-hospital transfers | `/api/v1/transfers/*` |
| **reviews** | Patient reviews and ratings | `/api/v1/reviews/*` |
| **portal** | Patient-facing portal summary | `/api/v1/portal/*` |
| **bulkimport** | CSV/Excel data migration | `/api/v1/bulkimport/*` |
| **ai** | General AI assistant queries | `/api/v1/ai/*` |

---

### Frontend Pages (apps/web/app/)

| Path | Role | What It Shows |
|------|------|--------------|
| `/dashboard/patient/` | Patient | Portal home — appointments, records, documents |
| `/dashboard/patient/documents/` | Patient | Document list, AI chat, summaries |
| `/dashboard/patient/documents/upload/` | Patient | Upload new document |
| `/dashboard/patient/appointments/` | Patient | Book and view appointments |
| `/dashboard/patient/lab-tests/` | Patient | Lab results with AI explanations |
| `/dashboard/patient/prescriptions/` | Patient | Active and past prescriptions |
| `/dashboard/patient/insurance/` | Patient | Insurance coverage, claims, pre-auth |
| `/dashboard/patient/invoices/` | Patient | Bills and payment status |
| `/dashboard/patient/chat/` | Patient | Secure messaging with doctor |
| `/dashboard/doctor/` | Doctor | Today's schedule and patient queue |
| `/dashboard/doctor/appointments/` | Doctor | Full appointment calendar |
| `/dashboard/doctor/patients/` | Doctor | Patient list and records |
| `/dashboard/doctor/documents/` | Doctor | Patient-uploaded documents |
| `/dashboard/doctor/documents/chat/` | Doctor | AI document chat for patient docs |
| `/dashboard/hospital/` | Admin | Hospital overview dashboard |
| `/dashboard/hospital/claims/` | Admin | Insurance claims monitor |
| `/dashboard/hospital/analytics/` | Admin | Revenue, occupancy, forecasting |
| `/dashboard/hospital/doctors/` | Admin | Doctor management and onboarding |
| `/dashboard/hospital/employees/` | Admin | HR and payroll management |
| `/dashboard/hospital/billing/` | Admin | Invoice and payment tracking |
| `/dashboard/reception/` | Reception | Check-in and queue management |
| `/dashboard/pharmacy/` | Pharmacy | Dispensing queue and inventory |
| `/meet/[id]` | All | Video consultation room |

---

## 8. AI & Document Intelligence

SmartClinic includes a complete AI-powered document processing pipeline. See the full guide at:

```
apps/api/docs/DOCUMENT_INTELLIGENCE.md
```

### Quick Summary

**What it does:**
1. Patient or staff uploads any medical document (PDF, JPG, PNG)
2. Tesseract OCR reads every page and extracts raw text
3. AI classifies the document type and pulls structured fields
4. Text is split into 800-character overlapping chunks stored in the database
5. Users ask questions in plain English
6. BM25 scoring finds the top 5 most relevant chunks
7. The AI generates a grounded answer with citations

**Supported AI Providers:**

| Provider | Config | Best For |
|----------|--------|---------|
| vLLM (Qwen2.5-Coder-7B) | `AI_PROVIDER=vllm` | On-premise, HIPAA-strict deployments |
| Claude (Anthropic) | `AI_PROVIDER=claude` | Highest accuracy, cloud-acceptable deployments |
| Local fallback | `AI_ENABLED=false` | Development and testing without AI |

**Supported Document Types:**
- Lab reports, discharge summaries, prescriptions
- Hospital bills, insurance EOBs, insurance cards
- Radiology reports, referral letters

**Example questions the AI can answer:**
- *"What medications was I prescribed and are there any drug warnings?"*
- *"What abnormal values are in this lab report?"*
- *"How much did my insurer pay and what do I still owe?"*
- *"What are my discharge instructions and follow-up dates?"*

---

## 9. Deployment

### Docker (Recommended for Production)

```bash
# Start the full stack
docker-compose up -d

# Services started:
# - PostgreSQL (port 5432)
# - Redis (port 6379)
# - API (port 8080)
# - Web (port 3000)
```

See `docs/cloud-deployment-guide.md` for full cloud deployment instructions (AWS, GCP, Azure).
See `docs/deployment-sizing-guide.md` for server sizing recommendations by hospital size.

### Environment Variables — Production Checklist

Before going live, ensure:

```
✅ JWT_SECRET — changed from default (use 64+ random chars)
✅ DB_PASSWORD — strong password, not exposed publicly
✅ AI_API_KEY — real vLLM key or Anthropic API key
✅ REDIS_ENABLED=true — for session management and job queues
✅ DOCUMENT_LOCAL_UPLOAD_PATH — points to a persistent volume
✅ PORT — behind a reverse proxy (Nginx or Traefik)
```

---

## 10. Roadmap & What's Next

### Near-Term (Next 3 Months)
| Feature | Priority | Description |
|---------|----------|-------------|
| Vector semantic search | High | Replace BM25 with embedding-based retrieval for document chat |
| Document sharing | High | Let patients share documents directly with specific doctors |
| S3 / Azure Blob storage | Medium | Move document storage off local disk for scalability |
| Insurance auto-filing | High | Direct API integration with BCBS, Aetna, UHC for claim submission |
| Push notifications | Medium | Mobile push for appointment reminders and lab results |

### Medium-Term (3–6 Months)
| Feature | Priority | Description |
|---------|----------|-------------|
| Mobile app (React Native) | High | iOS and Android patient app |
| Bulk document upload | Medium | Upload multiple documents at once with batch OCR |
| HL7 / FHIR integration | High | Exchange records with other hospital systems |
| Automated prior authorization | High | AI-generated pre-auth letters submitted to insurers |
| Predictive readmission risk | Medium | AI flags patients at high risk of readmission |

### Long-Term
| Feature | Priority | Description |
|---------|----------|-------------|
| Custom AI model fine-tuning | High | Train on hospital's own document corpus |
| Clinical decision support | High | AI suggests diagnoses and treatment options at point-of-care |
| Telemedicine marketplace | Medium | Connect patients with specialists outside their hospital |
| Population health analytics | Medium | Identify at-risk patient cohorts across the hospital |

---

## Appendix — Frequently Asked Questions

**Q: Does patient data ever leave the hospital?**
With the vLLM provider: No. OCR and AI processing run on your own infrastructure. With the Claude API provider: only anonymized text chunks are sent to Anthropic — no names, IDs, or PHI unless they appear in the document text.

**Q: How long does OCR + AI extraction take?**
Typically 5–20 seconds for a 2-page PDF: ~2–10 seconds for Tesseract OCR + 3–10 seconds for AI extraction via vLLM.

**Q: Can we use our existing EMR data?**
Yes — the bulk import module accepts CSV and Excel. Contact the implementation team for field mapping.

**Q: How is multi-tenancy enforced?**
Every database query is scoped to `hospital_id`. There is no shared data between hospitals at the application layer, and the middleware validates hospital ownership on every request.

**Q: What happens when a document has poor scan quality?**
The confidence score drops below 0.80 and the document is flagged for manual review. Staff can verify or reject the AI extraction through the verification workflow.

**Q: Can we self-host the AI model?**
Yes. The vLLM provider supports any OpenAI-compatible model server. We've tested with Qwen2.5-Coder-7B-Instruct on an A100 GPU. The AI model, OCR engine, and database all run on your own hardware.

---

*SmartClinic Master Guide | Version 1.0 | May 2026*
*For support: kumar@ginilytics.com*
