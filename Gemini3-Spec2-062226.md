Executive Summary & Design System
Overview
This technical specification details the architecture, design token system, state mechanics, and advanced algorithmic capabilities of the MedRegis 515(k) Agentic Workspace. Developed as a specialized, high-fidelity pre-market regulatory review platform, this application establishes a collaborative workspace where regulatory officers and AI agents co-audit US FDA 510(k) and Taiwan TFDA submissions.
The platform is designed to transition regulatory auditing from manual, document-heavy workflows to an optimized, agent-supported validation pipeline. By leveraging a structured single-screen layout with multiple coordinate working panels, the workspace minimizes cognitive overhead, enforces rigorous validation criteria, and surfaces hidden compliance vulnerabilities through custom automation subsystems.
Design System: The "Professional Polish" Aesthetic
The user interface is governed by custom design guidelines, avoiding default elements in favor of custom-styled components, high-contrast states, and clear spatial layouts.
code
Code
┌────────────────────────────────────────────────────────┐
                    │                      TOP NAVIGATION                    │
                    └────────────────────────────────────────────────────────┘
                    ┌──────────────┬──────────────────────────┬──────────────┐
                    │              │                          │              │
                    │  DOSSIERS    │      AGENT CONTROL       │   AI INSIGHT │
                    │      &       ├──────────────────────────┤   DASHBOARD  │
                    │   ACTIVE     │                          │              │
                    │   SKILLS     │   INTERACTIVE REPORT/    │   (6 GRAPHS) │
                    │              │        CHECKLIST         │              │
                    │              │                          │              │
                    └──────────────┴──────────────────────────┴──────────────┘
                    ┌────────────────────────────────────────────────────────┐
                    │                     BOTTOM STATUS BAR                  │
                    └────────────────────────────────────────────────────────┘
Typography Scale
To maintain readability and clean information design, we employ a three-tier type scale:
Display Typography (Space Grotesk): Chosen for headers and system branding. Its geometric form factor provides a "tech-forward," highly precise feeling.
Body & Controls UI (Inter): Applied across all tables, checklists, input blocks, and descriptive microcopy. Inter's optical optimization ensures legibility at small sizes (10px–12px).
Data & Telemetry Telemetry (JetBrains Mono): Utilized exclusively for logs, code panels, raw addresses, hashes, and clinical mathematical metrics.
Color Palette (Tailwind Tokens)
The canvas uses a high-contrast dark palette for the workspace shell, paired with a clean, high-contrast light theme for the primary workspace reporting panel:
Layer	Custom Utility	Target UI Application
System Background	bg-slate-950	Primary application boundary container
Primary Navigation	bg-slate-900	Navigation, structural borders, header elements
Borders	border-indigo-950/40	Inner layout divisions
Workspace Canvas	bg-slate-5	Main document pane, checklist canvas
Workspace Cards	bg-white	Checklist item card containers, inputs
Primary Accent	bg-indigo-600	Primary action buttons, active tab indicators
Highlight Glow	glow-indigo	Custom drop shadow with rgba(99, 102, 241, 0.15)
Success Feedback	bg-emerald-500	Pass badges, normal system status markers
Success Glow	glow-emerald	Glowing wrapper shadow with rgba(16, 185, 129, 0.15)
Warning/Danger	text-rose-500	Mismatch notices, data contamination warning
Workspace Layout & Panel Architecture
The user interface utilizes a fluid single-screen structure that scales dynamically across resolutions while maintaining strict boundaries to prevent scroll nesting conflicts.
code
Code
+-------------------------------------------------------------------------------------------------------------+
|  MedRegis 515(k) Agentic Workspace                                                      [Selected: gemini]  |
+-------------------------------------------------------------------------------------------------------------+
| DOSSIERS & ACTIVE SKILLS         | AGENT telemetry CONTROL logs & MODEL SELECTION                           |
| [1. Material List Component]     | [3. Agent Execution Terminal & Pipeline Trackers]                        |
|                                  +--------------------------------------------------------------------------+
| - device_spec.txt                | REGULATORY WORKSPACE (INTERACTIVE CHECKLIST PANELS)                      |
| - certificate.md                 | [4. Review Checklist / Category Explorer Component]                      |
| - lab_report.json                |                                                                          |
|                                  |   (All categories map to distinct laws)                                  |
| +------------------------------+ |                                                                          |
| | AI INSIGHT GRAPHS            | | - Clause 1-2 (Product Name Alignment)             [ PASS / FAIL / N/A ]  |
| | [2. Dashboard Component]     | | - Clause 1-6 (Manufacturing Sourcing Validity)    [ PASS / FAIL / N/A ]  |
| |                              | |                                                                          |
| |   Gauge / Heatmap / Overlap  | +--------------------------------------------------------------------------+
| |   Radar / Pulse / Scorecard  | REPORT EXPORT MATRIX                                                       |
| +------------------------------+ | [5. Exporter Hub Component (Markdown, Draft document, Raw PDF layout)]     |
+-------------------------------------------------------------------------------------------------------------+
| System Active - SHA-Hash                                                       TFDA Premium Workspace Approved |
+-------------------------------------------------------------------------------------------------------------+
1. Header Navigation Bar (Navigation Toolbar)
Sizing: Height: 3.5rem (h-14), fixed positioning at top.
Styling: bg-slate-900, defined with a thin border on the bottom (border-b border-indigo-950/40).
Interactive Triggers: Top bar houses the active execution actions and a display for the selected large language model.
2. Left-Hand Drawer / Utility Rail (Sidebar Controller)
Sizing: Width: 20rem (w-80) under desktop viewport, wrapping fluidly to full width for mobile viewports.
Capabilities: Dual-pane utility controller. Handles dossier file catalogs, and manages the execution ruleset script (skill.md).
Dossier Material Manager: Integrated interface displaying file sizes, mime types, and upload timestamps. Features a custom single-file creation controller directly within the UI.
Embedded Metrics Dashboard (Dashboard Panel): A visual panel displaying six live metric visualizations of the AI agent's analysis.
3. Agent Telemetry Control Center (Telemetry Display)
Sizing: High-density coordinate display, containing the active large language model selections and live execution timelines.
Live Terminal Terminal: Engineered with a deep-black base configuration (bg-[#0d1117]), monospace fonts, and automatic vertical scroll anchors. Standardizes operational debugging by assigning clear visual colors to runtime markers:
[INFO]: Technical scan telemetry, marked in light corporate blue.
[WARN]: Multi-agent spelling variations, marked in hazard warning amber.
[AGENT]: Semantic engine orchestration processes, marked in indigo.
[SUCCESS]: Passed checklist rules and clear data assertions, marked in emerald.
[ERROR]: High-risk data leaks and regulatory failures, marked in red.
4. Interactive Report Canvas (Workspace Pane)
Sizing: Responsive flex container displaying a dual-axis layout.
Component Coordination: Houses the formal regulatory checklist, administrative address aligning systems, and ML software validation panels. Includes status selectors and note fields for each checklist item.
5. Report Exporter Hub (Export Panel)
Sizing: Multi-column panel positioned at the footer of the document workspace.
Capabilities: Formats verified evaluations into Markdown files, drafted official document public texts, and printable single-page HTML layouts optimized for PDF export.
Core System Mechanics & State Configurations
The application's interactions are backed by a structured state design using safe TypeScript interfaces.
code
Code
┌───────────────────────┐
                          │     User Interaction  │
                          └───────────┬───────────┘
                                      │
                         [Trigger Execute Review]
                                      │
                                      ▼
                        ┌──────────────────────────┐
                        │ App.tsx: Orchestration   │
                        └─────────────┬────────────┘
                                      │
                 ┌────────────────────┼────────────────────┐
                 ▼                    ▼                    ▼
     ┌───────────────────────┐ ┌───────────────┐ ┌───────────────────┐
     │  Multi-Agent Address  │ │  SaMD Model   │ │  Dataset Leakage  │
     │  Reconciliation       │ │  Audit Matrix │ │  Cross-Audit      │
     └───────────┬───────────┘ └───────┬───────┘ └─────────┬─────────┘
                 │                     │                   │
                 └────────────────────┼────────────────────┘
                                      │
                                      ▼
                        ┌──────────────────────────┐
                        │   Unified ReviewStates   │
                        └─────────────┬────────────┘
                                      │
                        ┌─────────────▼────────────┐
                        │ Dashboard / Report UI    │
                        └──────────────────────────┘
TypeScript Data Interfaces
The core data layer uses the following specific interfaces to model the workspace state:
code
TypeScript
export interface SubmissionMaterial {
  id: string;
  name: string;
  type: 'txt' | 'md' | 'json' | 'pdf';
  content: string;
  size: string;
  uploadedAt: string;
}

export interface ChecklistItem {
  id: string;
  text: string;
  note?: string;
  categoryId: string;
}

export interface ReviewState {
  status: 'pass' | 'fail' | 'na' | 'pending';
  note: string;
  aiSuggested?: 'pass' | 'fail' | 'na' | 'pending';
  aiConfidence?: number;
  aiExplanation?: string;
  manualOverride?: boolean;
}

export type ReviewStates = Record<string, ReviewState>;

export interface DiscrepancyItem {
  id: string;
  field: string;
  sourceAName: string;
  sourceBName: string;
  valueA: string;
  valueB: string;
  confidence: number;
  status: 'unresolved' | 'resolved' | 'ignored';
  reconciliationAction?: string;
}
App State Flow Graph
The data flow is orchestrated at the parent level (App.tsx), managing sub-component updates via state variables.
Materials Ingestion: The system reads dossier files (e.g., text specifications, JSON metadata).
Execution Trigger: The user starts the AI review. The system progresses through sequential analysis pipelines and appends diagnostic records to the live telemetry logs.
Core Parameter Diagnostics:
Matches address string configurations.
Parses SaMD model variables for continuous updates.
Calculates mathematical overlaps between training and testing sets.
Interactive Mapping: Results are injected into ReviewStates to present suggested statuses (Pass/Fail) and ground truth matches.
Human Override and Annotation: The regulatory officer adjusts statuses and adds review notes.
Dynamic Dashboard Metrics: Radial compliance ratios, risk heatmaps, dataset overlap graphs, and discrepancy scorecards update in real-time.
Report Export: Users compile results into Markdown, draft templates, or print/save as PDF.
Active AI Core Orchestrator (Built-in Engines)
The agent uses three automated diagnostic modules to analyze uploaded dossiers.
Module 1: Multi-Agent Discrepancy Reconciliation Engine
Objective: Identify errors across disjointed sub-dossiers representing manufacturer entities and addresses (e.g., TFDA Application form vs. US Free Sale Certificates).
Execution: Computes semantic variations and structural naming anomalies (e.g., "Suite 401" vs "4F, Rm 401") to catch unregistered address changes.
Workflow:
Automatically identifies manufacturer address discrepancies across files.
Suggests corrective steps (e.g., aligning to approved address certificates).
Module 2: Continuous-vs-Locked Algorithm Audit Matrix
Objective: Target Machine Learning Software as a Medical Device (SaMD) to review its training architecture and update path.
Execution: Scans codebase parameters for "adaptive learning" markers.
Workflow:
Flags the absence of a "Post-Market Performance Monitoring and Verification Protocol" if adaptive updates are detected.
Automatically drafts a custom deficiency notice for the manufacturer:
code
Code
【TFDA 軟體審查補件不准條款 - 臨床前測試缺失】
經查與測試報告第 JSON 頁，該產品之演算法具有適應性(Adaptive)動態隨機學習矩陣。因其屬持續上市後自主更新，查案卷內欠缺建立「上市後性能監測與驗證機制」，恐有臨床不確定性。請說明並提供演算法動態確效監控方案。
Module 3: Deep Dataset Contamination Detector
Objective: Audit the statistical isolation between software training and testing datasets.
Execution: Checks mathematical metadata schemas and patient indexes in test reports.
Workflow:
Identifies overlapping patient identifiers (
) that can compromise evaluation validity.
Prompts clean retraining guidelines and dataset quarantine recommendations:
code
Code
Overlap Ratio Detected: 14% (420 Patients Leaked)
Action Required: Quarantine overlapping patient profiles. Retrain Convolutional Neural Network (CNN) weights from initial epoch. Export fresh validation reports ensuring complete mathematical isolation.
High-Utility AI Enhancements
To expand MedRegis's analysis capabilities, we present three advanced, high-utility agentic workflows under this specification.
code
Code
+-----------------------------------------------------------------------------------------+
| NEW AGENTIC ENGINE ADDITIONS                                                            |
+-----------------------------------------------------------------------------------------+
|                                                                                         |
|  [4. Bio-Compatibility Ontology mapping] --> Evaluates materials against ISO 10993     |
|                                                                                         |
|  [5. Multi-Modal Labeling Artwork Checker] --> Audits user guides for TFDA warnings      |
|                                                                                         |
|  [6. Cybersecurity SBOM threat modeling]  --> Scans package dependencies for vulnerabilities|
|                                                                                         |
+-----------------------------------------------------------------------------------------+
Module 4: Bio-Compatibility Semantic Ontology Cross-Audit (ISO 10993 Mapping)
System Concept: Evaluates physical materials of a device against patient contact configurations, mapping compliance directly to ISO 10993 standards and FDA G95-1 guidelines.
Underlying Mechanism:
An NLP parser extracts raw component lists from material specifications (e.g., silicone elastomer channels, SLA resins, stainless steel needles).
The system maps the contact category (e.g., external communicant, mucosal membrane, tissue/bone) and duration of exposure (Limited 
, Prolonged 
 to 
, Long-term 
):
The catalog is mapped against the ISO 10993-1 safety matrix to determine required biological tests (e.g., Cytotoxicity, Sensitization, Intracutaneous Reactivity, Genotoxicity).
Compliance Output:
Identifies missing test reports from laboratory submissions.
Flags incompatible materials used in high-risk zones (e.g., unapproved plasticizers in blood-contact paths).
Module 5: Multi-Modal Labeling & IFU Contraindication Checker
System Concept: Analyzes user manuals, catalogs, and packaging artwork against therapeutic claims and contraindications.
Underlying Mechanism:
Compares raw descriptions in User Guides (IFU) against cleared predicate devices.
Parses text to flag claims that exceed the device's technical specifications.
Audits the labeling layout to ensure mandated warning strings are present:
Required Warning String	Medical Device Context (Predicate Check)
"Pacemaker Interference Hazard"	Active electrical devices, surgical instruments, MRI-guided diagnostics.
"Contraindicated for Pediatric Use"	Diagnostic imaging software lacking pediatric training validation.
"Single-Use Only"	Disposable catheters, direct contact guide needles.
Compliance Output:
Reports mismatched text, conflicting instructions, and missing warning labels.
Automatically drafts updated warning copy for packaging artwork.
Module 6: Cybersecurity Threat Modeling & Dynamic SBOM Auditor
System Concept: Audits Software Bill of Materials (SBOM) and security protocols for connected devices and Software as a Medical Device (SaMD).
Underlying Mechanism:
Parses Software specifications to extract component trees, including open-source libraries, firmware operating systems, and communication endpoints (e.g., Bluetooth LE, TLS sockets).
Cross-references component lists against active vulnerability registries (NVD, CVE databases).
Audits the architecture for compliant security controls (e.g., SHA-256 validation, encrypted logging, secure boot paths).
Compliance Output:
Flags high-severity vulnerabilities (CVSS 
) within embedded software.
Generates a formatted CycloneDX SBOM, ensuring compatibility with FDA pre-market cybersecurity guidelines.
Technical Performance & Execution Parameters
To ensure responsive and reliable performance in the preview environment, the platform operates under specific architectural guidelines:
Performance Benchmarks
Asset Weight Limit: Raw React bundles and icon libraries are optimized to load within standard performance budgets.
Analysis Runtime: Simulated agent processing timelines run on controlled delay intervals (1200ms - 1800ms steps) to manage server-side execution overhead while providing immediate UI updates.
Memory Footprint: Components minimize render cycles through optimized state hooks. All static reference configurations (such as TFDA laws) are stored in decoupled module structures.
Local Storage Synchronization
The platform saves ongoing reviews locally, preventing loss of progress from page refreshes.
code
TypeScript
// State preservation logic
export function saveWorkspaceState(reviewStates: ReviewStates): void {
  try {
    localStorage.setItem('med_regis_states_v2', JSON.stringify(reviewStates));
  } catch (err) {
    console.error('Failed to protect workspace state', err);
  }
}

export function loadWorkspaceState(): ReviewStates {
  try {
    const raw = localStorage.getItem('med_regis_states_v2');
    return raw ? JSON.parse(raw) : {};
  } catch (err) {
    return {};
  }
}
Development Milestones
The roadmap outlines the steps required to progress the workspace integration to full production status.
code
Code
Phase 1: Foundation (Current)     Phase 2: Full Services           Phase 3: Clinical Validation
[Client Space Complete]          [External REST Endpoints]        [Official Testing Suite]
  - Inter active checklist         - Connect real API endpoints     - Audit logs for auditors
  - Live local dashboard           - Multi-user authentication      - Cloud database backup
  - Core system evaluations        - PDF rendering engines          - Clinical trial checks
Objective 1: Multi-User Collaboration: Integrate Firestore to support real-time shared reviews among regulatory team members.
Objective 2: Document Parsing (OCR): Connect server-side optical character recognition (OCR) and PDF parsers to extract structured text directly from scanned dossiers and physical Free Sale sheets.
Objective 3: API Integration: Implement secure routes back to actual Gemini LLM endpoints using the official @google/genai package for live, non-simulated analysis.
System Discussion: 20 Engineering & Regulatory Questions
To guide future reviews, architectural updates, and technical modifications of the workspace, evaluate the following structural and design considerations:
1. Architectural & Local State Scalability
When checking a dynamic registration with over 5,000 regulatory rows (such as multi-model cardiac catheter sets), does storing all checkbox parameters as a single flat ReviewStates record cause interface delay under React 18? Should we divide the checklist states by chapter into local caches?
2. Multi-Agent Address Alignment Thresholds
How can we adjust the Levenshtein string distance algorithm to avoid flagging acceptable variations (such as "Avenue" vs. "Ave." or "4th Floor" vs. "4F") while still catching critical, unnotified moves to new manufacturing locations?
3. Verification Dataset Overlap Mitigation
When the system flags patient profile overlap between training and testing sets, does it query source files to report the specific leaked data fields (e.g., patient age, scans, clinic locations), or should it quarantine only based on the primary key (Patient ID)?
4. Dynamic Ruleset (skill.md) Security Sandbox
If a user updates the active auditing script with malicious directives (e.g., forcing the system to automatically pass all bio-compatibility checks), what security measures prevent these overrides from bypassing standard regulatory safety rules?
5. Multi-Modal Artwork Verification
Does the Multi-Modal Packaging artwork auditor verify physical layout structures (such as font size limits, warning label placement, and safe bleed zones), or does it analyze only extracted text patterns?
6. Relational vs. Document Cloud Architecture
When migrating the platform from offline-first local storage to persistent database sync, is a relational database (PostgreSQL via Cloud SQL) better for tracking structured checklist versions, or is a document database (Firebase Firestore) more suited for unstructured dossier uploads?
7. Regulatory Version Synchronization
How does the platform handle updates to underlying food and drug laws (e.g., when the TFDA updates its Quality Management System guidelines)? How can we update active rulesets without overwriting historical audit determinations?
8. Cybersecurity SBOM Dependency Tracking
For connected medical devices, should the Cybersecurity Threat Module integrate with external vulnerability databases (such as Snyk or Sonatype) to monitor active library vulnerabilities, or should it run on static, point-in-time checks of the CycloneDX manifest?
9. PDF Layout Output Accuracy
When exporting review reports via the Printable HTML module, does page breaks split critical tables across sheets? Should we add custom CSS print styling to prevent table row truncation during PDF generation?
10. Multi-Language Regulatory Mapping
When cross-referencing foreign dossiers (e.g., Japanese, Korean, or EU certificates) with Taiwan regulations, how do we handle differences in regulatory terminology without losing accuracy in technical review notes?
11. Large Language Model Selection Benchmarks
For complex technical analyses (such as auditing biocompatibility test reports), does the slower, higher-capacity model outperform the faster model by enough to justify the increased latency and API costs?
12. Audit Trail & Human Override Logs
How should we structure audit logs when a regulatory officer overrides an AI-generated Fail suggestion to a Pass? What compliance data must be captured to justify and document this manual override?
13. Edge Cases in Adaptive Machine Learning
If an adaptive model updates continuously using clinician feedback, does the workspace monitor real-time update vectors, or does it evaluate only the initial post-market verification protocol submitted during registration?
14. Network Congestion & Timeout Handling
When uploading large dossier files (e.g., scanned manuals or extensive technical test dossiers), how should the frontend manage connection timeouts and display progress to the user during long-running background analysis tasks?
15. Offline-First Synchronization Conflicts
If an auditor works offline on a checklist, how does the system resolve conflicts when they reconnect and sync with collaborative, team-updated regulatory worksheets?
16. Patient Data Anonymization Safeguards
Before dossiers are sent to server-side LLM models for analysis, what validation checks should be run on the client side to identify and redact personal health information (PHI) or personal identifiable information (PII)?
17. Multi-Modal Visual Verification
In the label auditor, does the system process artwork as structured layouts, or does it evaluate only OCR text? How do we handle low-resolution images or stylized fonts that are difficult for standard OCR models to parse?
18. API Cost Allocation Models
What rate limiting or token allocation policies should we implement to prevent a single user from incurring excessive API costs when executing reviews on very large dossier packages?
19. Integration with Enterprise QMS Systems
How can we design the API layer to allow MedRegis reports and audit findings to export directly to existing enterprise Quality Management Systems (such as Veeva, Arena, or Greenlight Guru)?
20. Legal Liability of Automated Recommendations
When the AI system suggests a Pass/Fail determination, how do we clearly frame the responsibility of the review (e.g., that suggestions are non-final recommendations requiring final human review) to meet health authority liability guidelines?
