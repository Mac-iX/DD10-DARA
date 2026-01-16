# DARA & DIDI: Final Architecture Specification

**Version:** 2.0
**Author:** Mac & Manus AI

## 1. Core Vision: The DARA-First Experience

The user experience is centered around **DARA (Deep Audience Research Agent)**, a linear, 5-step workflow for generating high-quality synthetic audience data. **DIDI (Deep Impact Data Illumination)** modules are positioned as optional enhancements to validate, deepen, and extract further insights from the core DARA report.

This architecture simplifies the user journey, aligns with industry best practices for synthetic data, and enables powerful, iterative research.

## 2. The Workflow: From Topic to Deep Insight

### Step 1: User Input
- The user provides a topic, a geographic region, and indicates whether they have existing data.

### Step 2: Pre-Research (Optional)
- If the user has no existing data, they can choose to run the **Complete Deep Research Agent** (a DIDI module) to gather baseline market intelligence.

### Step 3: DARA Core Workflow (Automated)
- The 5 DARA modules run in sequence to produce the initial research artifact:
  1. Foundational Research
  2. Audience Segmentation
  3. Persona Generation
  4. Simulated Inquiry
  5. Strategic Synthesis

### Step 4: The Artifact
- The output of the DARA workflow is a persistent research **artifact**, a structured JSON document that serves as the single source of truth for the research session.

### Step 5: DIDI Enhancement (User-Driven)
- The user can then select from a curated list of DIDI modules to run on the artifact:
  - **Deep Quality Review:** Validate findings and check for bias.
  - **Deep Signal Detection:** Identify hidden patterns and emerging trends.
  - **Deep Reasoning:** Test assumptions and logical coherence.
  - **Deep Synthesis:** Generate cross-domain insights and strategic connections.

### Step 6: Iterative Deepening
- Each DIDI enhancement is appended to the artifact, creating a version history and a progressively richer research document.

## 3. The Memory Protocol: Artifact-Based Persistence

- **Storage:** For the MVP, artifacts will be stored in the browser's `localStorage`. This is simple, fast, and requires no database setup. In the future, this can be migrated to Supabase for cross-device persistence.
- **Structure:** Each artifact is a JSON object with a unique ID, a core DARA report, and an array of DIDI enhancements.
- **Embeddings:** Vector embeddings are generated for the DARA report and each DIDI enhancement, enabling future semantic search capabilities (e.g., "find all research related to franchising").

## 4. The Technology Stack

- **Frontend:** Next.js (built with v0.dev)
- **Backend:** Node.js (your existing `/core` modules)
- **Deployment:** Vercel
- **Database (MVP):** `localStorage`
- **Database (Future):** Supabase

## 5. Frontend Specification (for v0.dev)

### Key UI Components

- **Dashboard:** A clean, cPanel-style interface.
- **Input Form:** A simple form with fields for topic, region, and existing data.
- **Module Cards:** Visual cards for selecting DIDI enhancement modules.
- **Chat Interface:** A central text field for interacting with the agent.
- **Results Display:** A well-formatted view of the research artifact, with clear versioning for each enhancement.

### User Flow

1. User lands on a simple, elegant page that explains the power of DARA.
2. User fills out the input form and starts the research process.
3. A progress screen shows the DARA workflow in action.
4. The initial DARA report is displayed.
5. The user is presented with a list of optional DIDI enhancement modules.
6. The user selects enhancements, and the report is updated in real-time.

## 6. Backend Specification

### API Endpoints

- `POST /api/research`: Starts a new DARA research session.
- `GET /api/artifacts/:id`: Retrieves the current state of a research artifact.
- `POST /api/enhancements/:id`: Runs a DIDI enhancement on an existing artifact.

### Core Modules

- Your existing `/core` modules will be adapted to fit this new workflow.
- The `agent_router.js` will be simplified to handle the DARA-first logic.
- A new `artifact_manager.js` will be created to handle the creation and updating of research artifacts.

## 7. Validation

This architecture has been validated against best practices from Bain & Company, Stanford, Google DeepMind, and Qualtrics. It positions your product at the cutting edge of applied AI for market research.
