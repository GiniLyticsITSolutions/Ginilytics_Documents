# AI-Powered CRM Portal — Complete Product & Technical Documentation

> **Version:** 1.0 | **Stack:** Next.js 14 · Supabase · OpenAI GPT-4o-mini · Tailwind CSS

---

## Table of Contents

1. [What Is This Platform?](#1-what-is-this-platform)
2. [Who Does It Help & How?](#2-who-does-it-help--how)
3. [Feature Modules](#3-feature-modules)
4. [Role-Based Access Model](#4-role-based-access-model)
5. [Data Flow: Lead → Client → Delivery](#5-data-flow-lead--client--delivery)
6. [AI-Powered Capabilities](#6-ai-powered-capabilities)
7. [Database Schema Overview](#7-database-schema-overview)
8. [Tech Stack](#8-tech-stack)
9. [Environment Setup](#9-environment-setup)
10. [Deployment](#10-deployment)
11. [Security Model](#11-security-model)
12. [What Needs to Be Done (Roadmap)](#12-what-needs-to-be-done-roadmap)

---

## 1. What Is This Platform?

This is a full-stack, AI-powered CRM (Customer Relationship Management) portal purpose-built for **Business Consulting companies** that provide:

- **Strategic Advisory**
- **Business Development**
- **Project Management**
- **Funding Acquisition (Government Grants, Loans, Tax Credits)**

The portal acts as a **single centralized hub** for both the internal team and their clients — replacing scattered spreadsheets, email threads, and disconnected tools with one secure, intelligent platform.

---

## 2. Who Does It Help & How?

### Clients
Clients get a private, professional portal where they can:
- **See the live status** of their projects in real time — no more chasing emails
- **Access and upload documents** in organized, secure folders specific to their account
- **Communicate directly** with their assigned team members through in-app messaging
- **Find government funding** opportunities tailored to their company using an AI-powered funding tool
- **Track deliverables** and approve milestones from a dedicated workspace

**Value:** Clients feel informed, in control, and professionally served at all times.

---

### Team Members
The internal consulting team can:
- **Manage leads** from first contact all the way to a signed contract — without losing context
- **Kick off projects** from templates as soon as a lead converts, automatically setting up workspaces and tasks
- **Collaborate on projects** with clients and colleagues inside dedicated shared workspaces
- **Track every deliverable**, assign tasks, and monitor progress on a single dashboard
- **Use AI tools** to draft emails, summarize documents, extract action items from meetings, and score leads
- **Search the entire CRM** in natural language (e.g. "Show me all leads over $50k in tech")

**Value:** The team spends less time on administration and more time delivering results.

---

### Admins
Admins get full visibility and control:
- **Manage all users**, assign roles, and onboard new team members or clients
- **View analytics** across all leads, projects, opportunities, and clients
- **Access every workspace** and audit all activity
- **Configure the system** through the admin panel

**Value:** Leaders have a real-time command center for the entire business.

---

## 3. Feature Modules

### Dashboard
- Personalized overview of active projects, leads, and key metrics
- Progress bars for ongoing projects
- Quick-access widgets for recent activity, tasks due, and new messages
- Role-specific views (Admin sees company-wide stats; Clients see only their data)

---

### Lead Management
Track every potential client from first touch to signed contract.

| Pipeline Stage | Description |
|---|---|
| **New** | Lead entered into system |
| **Contacted** | Initial outreach made |
| **Qualified** | Vetted and assigned to the relevant business unit |
| **Proposal Sent** | Proposal or RFP submitted |
| **Negotiation** | Terms being discussed |
| **Won** | Client signed — triggers project/workspace creation |
| **Lost** | Lead did not convert |

- Add **notes** at every stage
- **AI Lead Scoring** predicts conversion probability (0–100%)
- Assign leads to specific team members
- Track lead **source**, **deal value**, and **industry**

---

### Project Management
- Create projects from **templates** (e.g. Funding Strategy, RFP Response, Grant Application, Market Entry)
- Set **start/end dates**, track **progress %**, and update **status**
- Break projects into **milestones and tasks**
- Assign tasks to team members with due dates
- **AI Project Planning Assistant** suggests task breakdowns from a project description

Project statuses: `planning` → `in_progress` → `on_hold` → `completed` / `cancelled`

---

### Workspaces (Collaboration Hubs)
Every project gets a dedicated **Workspace** — a shared space for the team and client.

Each workspace contains:

| Tab | Purpose |
|---|---|
| **Overview** | Summary, status, team roster |
| **Tasks** | Assignable workspace-level tasks |
| **Documents** | Internal, Client, Final, Reporting folders |
| **Messages** | Threaded chat with @mentions |
| **AI Tools** | Context-specific AI assistants |

- Workspace membership is **controlled** — only invited users can see the workspace
- Clients only see their own workspace; they cannot see internal communications

---

### Document Management
- Organized **folder hierarchy** (nested folders per client/project)
- **Secure file uploads** to Supabase Storage (private bucket)
- Support for PDF, Word, images, and other file types
- Files are **scoped by user/workspace** — full Row Level Security
- **AI Document Intelligence**: extract key info, auto-summarize, tag documents

---

### Messaging
- **Direct messages** between any two users
- **Workspace chat** visible to all workspace members
- Messages are scoped by security — clients cannot see internal team chats
- **AI Smart Reply**: suggests professional responses based on conversation context

---

### Government Funding Finder (AI Tool)
A flagship feature that sets this platform apart from generic CRM solutions.

Clients or team members input basic company information:
- Company name, industry, employee count, annual revenue
- Country and region (Canada or USA)
- Brief description of business activities

The AI then searches and matches the company against:
- Canadian Federal: Innovation, Science & Economic Development Canada
- All Provincial Funding Programs (ON, BC, AB, QC, etc.)
- US Federal Agencies: SBA, USDA, DOE, DOD, NSF, and more
- State-level funding bodies (Department of Commerce, Agriculture, etc.)

Results include grants, loans, tax credits, and incentive programs with eligibility criteria.

All searches are **saved** to the user's history for future reference.

---

### Opportunity Pipeline
For teams that pursue government contracting and RFP opportunities:

- Track **RFPs and tenders** sourced from government portals
- Score each opportunity: **Fit Score**, **Complexity**, **Competitive Rating**, **Overall Score**
- Move opportunities through a pipeline: `Identified` → `Evaluating` → `Pursuing` → `Submitted` → `Won`/`Lost`
- **Won** status auto-creates a project and workspace

---

### Vendor Registrations
Track client registrations with government procurement agencies:
- Agency name, market, registration number, expiry date, status
- Link registrations to specific contracting opportunities
- Flag eligibility requirements before bidding

---

### Admin Panel
- **User management**: create, view, update, deactivate users
- **Role assignment**: Admin / Team Member / Client
- **System-wide visibility**: see all leads, projects, clients
- **Audit trail**: activity timestamps on all records

---

### Settings
- Update personal profile (name, avatar)
- Notification preferences
- Account security

---

## 4. Role-Based Access Model

| Feature | Admin | Team Member | Client |
|---|:---:|:---:|:---:|
| View all leads | Yes | Yes | No |
| Manage leads | Yes | Yes | No |
| View all projects | Yes | Own only | Own only |
| Create projects | Yes | Yes | No |
| Access workspaces | Yes | Member of | Member of |
| View internal messages | Yes | Yes | No |
| Manage documents | Yes | Yes | Own only |
| Funding Finder | Yes | Yes | Yes |
| Opportunities/Pipeline | Yes | Yes | No |
| Vendor Registrations | Yes | Yes | No |
| Admin Panel | Yes | No | No |
| Manage all users | Yes | No | No |

---

## 5. Data Flow: Lead → Client → Delivery

```
LEAD CREATED
    |
    v
Lead Qualified (vetted and assigned to relevant business unit)
    |
    v
Pipeline Stages (Contacted -> Proposal -> Negotiation)
    |
    v
CLOSED WON --- AUTOMATION TRIGGERED -------------------------+
    |                                                         |
    v                                                         v
CLIENT Record auto-created                  PROJECT created from template
    |                                               |
    +----------------------+------------------------+
                           |
                           v
                 WORKSPACE auto-created
                 (Folders, Tasks, Members)
                           |
           +---------------+----------------+
           v               v                v
       DOCUMENTS       MESSAGES          TASKS
       (organized)    (team+client)   (from template)
                           |
                           v
                    DELIVERABLES
               (Draft -> Review -> Approved)
```

**Contracting Unit Parallel Path (Government RFPs):**
```
OPPORTUNITY FOUND -> PIPELINE ITEM CREATED -> SCORED
    |
    v
Pipeline: Identified -> Evaluating -> Pursuing -> Submitted
    |
    v
WON -> PROJECT auto-created -> WORKSPACE -> PROPOSAL DEVELOPMENT
```

---

## 6. AI-Powered Capabilities

| AI Feature | How It Helps |
|---|---|
| **Lead Scoring** | Predicts which leads are most likely to convert (0–100%) and suggests next actions |
| **Smart Email/Message Drafting** | Generates professional, context-aware drafts for client communications |
| **Document Intelligence** | Summarizes lengthy documents, extracts key information, suggests tags |
| **Project Planning Assistant** | Suggests task breakdowns and effort estimates from a project description |
| **Meeting Notes Extraction** | Paste meeting notes → AI extracts action items, owners, and deadlines → auto-creates tasks |
| **Client Insights Dashboard** | Highlights engagement trends, anomalies, and actionable recommendations |
| **Natural Language Search** | Search all CRM data with plain English queries |
| **Funding Finder** | Matches company profiles to relevant government grants, loans, tax credits across Canada & USA |

All AI features are powered by **OpenAI GPT-4o-mini** via the OpenAI API.

---

## 7. Database Schema Overview

Built on **Supabase (PostgreSQL)** with full **Row Level Security (RLS)**.

### Core Tables

| Table | Purpose |
|---|---|
| `profiles` | Extends Supabase Auth — stores name, avatar, role |
| `projects` | Project records with status, progress, dates |
| `project_members` | Many-to-many: users to projects |
| `tasks` | Tasks linked to projects, assigned to users |
| `workspaces` | Collaboration spaces linked to projects |
| `workspace_members` | Many-to-many: users to workspaces |
| `workspace_tasks` | Tasks specific to a workspace |
| `folders` | Hierarchical folder structure for documents |
| `documents` | File metadata + Supabase Storage URL |
| `messages` | Direct messages and workspace chat |
| `leads` | Lead pipeline with status and notes |
| `lead_notes` | Notes attached to leads |
| `funding_searches` | Saved funding finder searches and results |

### Custom Enum Types

| Type | Values |
|---|---|
| `user_role` | `admin`, `team_member`, `client` |
| `project_status` | `planning`, `in_progress`, `on_hold`, `completed`, `cancelled` |
| `lead_status` | `new`, `contacted`, `qualified`, `proposal`, `negotiation`, `won`, `lost` |

### Key Database Features
- **UUID primary keys** on all tables
- **Cascading deletes** to maintain referential integrity
- **Automatic `updated_at` timestamps** via PostgreSQL triggers
- **`handle_new_user()` trigger** auto-creates a profile on Supabase Auth signup
- **Private Storage Bucket** (`documents`) with user-scoped policies
- **Performance indexes** on all foreign keys and frequently filtered columns

---

## 8. Tech Stack

| Layer | Technology | Why |
|---|---|---|
| **Framework** | Next.js 14 (App Router) | Server components, API routes, SSR |
| **Database** | Supabase (PostgreSQL) | Managed Postgres, real-time, Auth, Storage |
| **Authentication** | Supabase Auth | Secure JWT-based auth out of the box |
| **AI** | OpenAI GPT-4o-mini | Fast, cost-effective, powerful LLM |
| **Styling** | Tailwind CSS | Rapid, consistent UI development |
| **Language** | TypeScript | Type safety across the full stack |
| **Deployment** | Vercel | Optimized for Next.js, global CDN |

---

## 9. Environment Setup

### Prerequisites
- Node.js v18+
- npm
- Git
- Supabase account (https://supabase.com/)
- OpenAI API key (https://platform.openai.com/api-keys)

### Step-by-Step

**1. Clone & Install**
```bash
git clone <repository-url>
cd CRM-project
npm install
```

**2. Create Supabase Project**
1. Go to app.supabase.com → New Project
2. In the SQL Editor, run `supabase/schema.sql` entirely
3. Copy your Project URL, anon key, and service_role key from Project Settings → API

**3. Create Admin User**
1. In Supabase: Authentication → Users → Add User (enable "Auto Confirm")
2. Then run in SQL Editor:
```sql
UPDATE profiles SET role = 'admin', name = 'Admin User'
WHERE email = 'your-admin@email.com';
```

**4. Configure Environment Variables**

Create `.env.local` in the project root:
```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project-id.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
OPENAI_API_KEY=sk-your-openai-key
```

> Warning: Never commit `.env.local` to version control.

**5. Run Locally**
```bash
npm run dev
```
Open http://localhost:3000

### Available Scripts

| Command | Purpose |
|---|---|
| `npm run dev` | Start development server |
| `npm run build` | Build production bundle |
| `npm run start` | Run production server |
| `npm run lint` | Run ESLint checks |

---

## 10. Deployment

### Deploy to Vercel (Recommended)

1. Push code to GitHub (ensure `.env.local` is in `.gitignore`)
2. Connect your GitHub repo at vercel.com
3. Add environment variables in Vercel → Project Settings → Environment Variables
4. Deploy — Vercel auto-detects Next.js and handles everything

### Post-Deployment Checklist
- [ ] Verify Supabase connection works from production URL
- [ ] Test authentication login/signup flow
- [ ] Confirm AI features respond (check OpenAI API credits)
- [ ] Test file upload/download via Supabase Storage
- [ ] Enable 2FA on Supabase and OpenAI accounts

---

## 11. Security Model

### Row Level Security (RLS)
Every table has RLS enabled. Key policies:

| Table | Rule |
|---|---|
| `profiles` | Anyone can view profiles; users can only update their own |
| `projects` | Only project members can view/edit their projects |
| `workspaces` | Only workspace members can access their workspaces |
| `documents` | Uploader owns their files; workspace members can view shared files |
| `messages` | Only sender/receiver or workspace members can see messages |
| `leads` | Only `admin` and `team_member` roles can access leads |
| `funding_searches` | Users can only see their own search history |

### Storage Security
- Documents stored in a **private** Supabase Storage bucket
- Storage policies enforce user-scoped access by folder name
- No public access to any files

### Best Practices
- All secrets stored in environment variables, never in code
- `SUPABASE_SERVICE_ROLE_KEY` only used server-side in API routes
- Strong password requirements for all admin accounts
- Enable 2FA on Supabase dashboard and OpenAI platform

---

## 12. What Needs to Be Done (Roadmap)

### Critical (Must Have)
- [ ] **Google Workspace Integration** — Gmail, Google Drive, Google Meet, Google Docs sync
- [ ] **Real-time notifications** — in-app alerts for new messages, task assignments, lead updates
- [ ] **Lead-to-Client Automation** — automatic creation of Client record, Project, and Workspace when a lead is marked "Won"
- [ ] **Client onboarding flow** — guided setup for new clients when they first log in

### High Priority
- [ ] **Funding Finder Enhancement** — integrate live government databases (ISED Canada API, SAM.gov, etc.) for real-time data
- [ ] **Project Templates** — pre-built task lists (Funding Strategy, Grant Application, RFP Response, Market Entry)
- [ ] **Deliverables Tracking** — milestone approval workflow (Draft → Internal Review → Client Approval → Final)
- [ ] **Opportunity Pipeline UI** — visual Kanban board for government contracting opportunities
- [ ] **Vendor Registration Module** — full UI for tracking government agency registrations

### Nice to Have
- [ ] **Mobile-responsive PWA** — works as an installable app on mobile devices
- [ ] **Analytics Dashboard** — lead conversion rates, project delivery metrics, BU-level reporting
- [ ] **Email integration** — send/receive emails directly from the CRM, linked to leads/clients
- [ ] **Calendar integration** — sync meetings with Google Calendar; view deadlines in calendar view
- [ ] **Bulk CSV import** — import leads or clients from spreadsheets
- [ ] **White-label client portal** — branded portal URL for each client

### Future
- [ ] **Multi-tenant support** — allow other consulting firms to use the platform
- [ ] **Automated reporting** — weekly/monthly PDF reports sent to clients automatically
- [ ] **E-signature integration** — clients sign proposals and contracts within the portal
- [ ] **AI meeting transcription** — auto-transcribe Google Meet calls and extract action items

---

> This documentation should be kept up to date as new features are built.
> Last updated: May 2026
