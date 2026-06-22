NEXUSREG 510(k) AGENTIC COMPLIANCE WORKSPACE
Comprehensive Technical & Systems Engineering Specification
code
Code
Document Ref: SYS-ENG-TFDA-510K-NEXUSREG
Classification: Enterprise Systems Architecture & Operations Blueprint
Target Infrastructure: Google Cloud Run (Fully Sandboxed, SSL Locked, Port 3000 Ingress)
Design Theme: High-Contrast Minimalist Editorial Aesthetic
1. Executive Summary & Product Vision
1.1 Product Statement
The NexusReg 510(k) Medical Device Regulatory Review Agent Workspace is an enterprise-grade compliance platform designed to automate, evaluate, and structure the regulatory auditing of medical device registration dossiers (the Traditional 510(k) pathway) in accordance with the Taiwan Food and Drug Administration (TFDA) regulatory directives and the official 醫療器材許可證核發與登錄及年度申報準則.
By ingesting complex, disjointed, and multi-format medical device submission packages (PDFs, raw text, Markdowns, and structured JSON schemas) alongside standard or custom executable regulatory review skills (formatted in Markdown with structured metadata), the system compiles a highly interactive, legally grounded, and physically accurate Regulatory Review Report.
Through an integrated full-stack workspace, regulatory affairs officers (RAOs) and TFDA reviewers can audit LLM-generated determinations, append custom reviewer notes, review advanced mathematical data leakage analyses, inspect address discrepancy metrics, and export final, decision-ready reports directly to Google Docs, Markdown, or print-ready HTML layouts.
code
Code
+---------------------------------------------------------------------------------+
|                               NexusReg Platform                                 |
+--------------------------+------------------------------------------------------+
| FILE INGESTION           | CORE AUDITING ENGINES                                |
| • JSON Schema Extraction | • 1. Jaro-Winkler Geographic Reconciler             |
| • Volatile PDF Stripping | • 2. SaMD Adaptive Weights Verification              |
| • Markdown Rules Token   | • 3. Cross-Dataset Frobenius Contamination Scan     |
|                          | • 4. Bilingual Semantic Cosine Alignment (NEW)       |
|                          | • 5. DAG-Based Dependency Hazard Matrix (NEW)        |
|                          | • 6. Benford-KS Report Authenticity Probe (NEW)     |
+--------------------------+------------------------------------------------------+
| RESULT BOARD             | VISUAL SUITE                                         |
| • Three-State Switch     | • 6 Interactive Recharts Visualizations              |
| • Local Persistency      | • Live Neural Map Execution Stream                   |
| • Export compilation     | • Fully Audited Draft Deficiency Letters             |
+--------------------------+------------------------------------------------------+
1.2 Administrative Alignment & Legislative Foundation
Under the Taiwan Medical Devices Management Act (醫療器材管理法) and the TFDA's Administrative guidelines, regulatory submission dossiers must undergo rigorous, multi-layered administrative and technical audits. Submissions are classified into eight primary legislative segments:
Administrative Information Verification (申請書資訊核對): Ensuring manufacturer names, addresses, and registrations strictly match.
China-Import Eligibility Filters (陸輸醫療器材與資格證明): Tracking CCC Codes and authorization lists.
Certificate of Free Sale & Manufacture Alignment (製售證明核對): Cross-verifying issuing timelines (under 2 years) and validation authorities.
Letter of Authorization Verifications (國外原廠授權登記書): Tracking agency relationships and expiration parameters (under 1 year).
Quality Management System Certification (品質管理系統證明/QSD/GMP): Matching Class scope and 3-year validation windows.
Contract Manufacturing Proofs (委託製造相關合約與證明): Validating legal obligations across supply lines.
Labelling and IFU Review Protocols (標籤、說明書及包裝擬稿): Standardizing warning codes, model specs, and local instructions.
Technical Safety and Performance Audits (技術審查資料): Processing clinical and hardware reports (such as electrical safety, biocompatibility, software verification, and algorithm parameters).
NexusReg maps technical data directly against this 8-chapter legislative baseline. By automating string metrics and mathematical dataset audits, the workspace isolates compliance discrepancies before dossiers are submitted to state departments, preventing lengthy regulatory holding patterns.
2. The Editorial Aesthetic Design Philosophy
NexusReg rejects the visual chaos of typical "AI applications" which are often decorated with neon lines, robotic status logs, and unnecessary structural blocks. Instead, the application implements a calculated Editorial Aesthetic inspired by classical Swiss print design journals, technical broadsheets, and editorial journals.
code
Code
[ Classical Editorial Typography Pairing ]
                       |
                       +---> Headers: "Lora" (Distinct Elegant Serif)
                       |     - Medium Tracking, Italic Accents, Refined Weight
                       |
                       +---> Functional Text: "Plus Jakarta Sans" (Geometric Clean Sans)
                       |     - Highly Legible, Minimal Width variation
                       |
                       +---> Metadata / Code: "JetBrains Mono" (Brutalist Tech Space)
                             - Used for metrics, data outputs, and live log buffers
2.1 Spatial Organization and the Power of Negative Space
The visual style is characterized by a high-contrast layout, utilizing a muted background canvas of soft cream and bone-white (bg-[#FAF9F6]) paired with dark charcoal text (text-[#1C1F2B]). Panels use crisp, single-pixel borders (border-[#EAEADF]) and very slight drop shadows to maintain a flat, structured appearance.
Generous padding and whitespace are employed as functional design elements rather than accidental margins. This helps guide the reviewer's focus to critical data points, while structural cards separate technical analyses cleanly without creating visual noise.
code
Code
+----------------------------------------------------------------------------------+
| PANEL LAYER (White - bg-white)                                                  |
|                                                                                  |
|  [H1 - Elegant Serif Lora]                                                       |
|  "Section 1: Administrative Discrepancy Reconciliation"                          |
|                                                                                  |
|  [Body - Plus Jakarta Sans]                                                      |
|  The system compares string tokens extracted from the Certificate of Free Sale    |
|  (CFS) and the local regulatory application index.                               |
|                                                                                  |
|  [Metrics - JetBrains Mono]                                                      |
|  Jaro-Winkler Score: 0.941 | Orthodromic Spatial Distance: 12.4m                 |
+----------------------------------------------------------------------------------+
2.2 Functional Accents & Brand Palette
Background Base: Soft Editorial Ivory (bg-[#FAF9F6])
Core Contrast Text: Deep Graphite (text-[#1C1F2B])
Compliance Success: Quiet Sage Teal (bg-teal-600, text-teal-900)
Compliance Deficiencies: Deep Muted Rose / Crimson (bg-rose-50/20, text-[#E11D48])
Warning States: Burnished Amber / Ochre (text-[#C58940])
System Accents: Editorial Indigo / Purple (text-[#4B3F72])
2.3 Structural Cleanliness: Anti-AI-Slop Code
Every interface element has a direct functional purpose. Border divisions align with standard print margins, interactive buttons scale responsively without shifting layouts, and raw metadata blocks are clearly formatted using tech-style monospace fonts to differentiate them from regulatory guidelines.
3. Global System Architecture & Full-Stack Implementation
NexusReg is built on a full-stack, secure cloud architecture. It runs a responsive React single-page application on the frontend, supported by a scalable Express server on the backend. This setup isolates processing loads and ensures that sensitive files are handled securely.
code
Code
+--------------------------------------------+
       |         React 19 Frontend Web App          |
       |     - Tailwind CSS v4 / custom pre-sets    |
       |     - Dynamic Recharts Data Suite          |
       |     - Local Volatile Ingestion Buffer      |
       +--------------------------------------------+
                             |
                             v [HTTPS Stream / JSON REST API]
       +--------------------------------------------+
       |         Node.js Express 4 Backend          |
       |     - Bound exclusively to Host: 0.0.0.0   |
       |     - Listening over Sandboxed Port 3000   |
       |     - High-capacity JSON payload limits    |
       +--------------------------------------------+
                             |
              +--------------+--------------+
              |                             |
              v                             v
  +-----------------------+     +-----------------------+
  |  Multi-Agent Engines  |     |   OAuth Integration   |
  |  - Jaro-Winkler Sim   |     |   - Firebase Auth     |
  |  - Frobenius Matrix   |     |   - Google Docs API   |
  |  - KS Statistical     |     |   - Cloud Drive Sync  |
  +-----------------------+     +-----------------------+
              |
              v [Secured with process.env.GEMINI_API_KEY]
  +-----------------------------------------------------+
  |          Google Gemini SDK Server-Side Calls        |
  |     - Model default: gemini-3.1-flash-lite          |
  |     - Escalate logic: gemini-3.1-pro-preview        |
  +-----------------------------------------------------+
3.1 Backend Server Configurations (server.ts)
The server runs on Express 4, configured with a 50MB payload limit to support parsing large technical reports and clinical trial files. It isolates analysis logic into key backend utilities, ensuring calculations like geocoding comparisons and Frobenius norm metrics are calculated efficiently.
To optimize frontend performance during complex analysis runs, calculations are divided into parallel tasks. This allows the system to process multiple checks concurrently and stream updates to the client interface.
3.2 Frontend Client Operations (src/App.tsx)
The React application coordinates user interactions across five primary views:
Source Ingestion Hub & Controls: Houses drag-and-drop zones, custom skill upload fields, model selectors, and analysis trigger buttons.
Dynamic Live Log & Neural Flow Terminal: Streams typewriter-style operational logs and connects analysis cards with interactive progress paths.
Interactive 8-Section Checklist Board: Exposes responsive click-to-toggle Pass/Fail/NA states, links checks directly to dossier items, and supports real-time editing of review notes.
Wow Metric Suite: Integrates 6 highly customized Recharts panels to visualize audit completeness, address offsets, and data leakage risks.
Autogenerated Corrective Deficiency Letter: Compiles reviewer findings into a structured template formatted in traditional TFDA legal phrasing.
3.3 Production Build Scripts & Deploy Systems (package.json)
To ensure compliance with Cloud Run's strict production build requirements, dependencies and build steps are defined as follows:
code
JSON
{
  "name": "nexusreg-agentic-suite",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "tsx server.ts",
    "build": "vite build && esbuild server.ts --bundle --platform=node --format=cjs --packages=external --sourcemap --outfile=dist/server.cjs",
    "start": "node dist/server.cjs",
    "lint": "tsc --noEmit"
  }
}
By utilizing esbuild to compile server.ts into a self-contained, consolidated CommonJS module (dist/server.cjs), the build pipeline bypasses Node's strict runtime ES Module checks. This ensures faster cold-start times, exports reliable sourcemaps, and cleanly packages output components for deployment.
4. Materials Ingestion & Parsing Services
4.1 Dossier Input Stream Sanitizer
The platform accepts multiple folder and document formats:
Structured JSON: Captures application characteristics, registration identities, and manufacturer records.
PDF Submissions: PDFs are handled securely using Node stream engines. Text is extracted from administrative papers and technical logs.
TXT & Markdown Packages: Handled via local buffers, preserving layout formatting.
4.2 Custom skill.md Executive Checklist Tokenizer
To map criteria without relying on hardcoded rules, ReguNexus uses an executable parser that reads compliance rules from markdown files.
Metadata Reader: Parses YAML metadata delimited by triple-dashes (---) to register the checklist identity.
Section Parser: Uses regex to translate Markdown H1/H2 headings into structured check metrics (incorporating indices like id, section_title, and clause_text). This lets users easily update regulatory checks by simply dropping in a new Markdown file.
5. Detailed Mathematical Specifications of Core AI Features
NexusReg goes beyond basic text parsing to implement six highly specialized, mathematically-validated AI validation engines.
code
Code
+--------------------------------------------------------------+
       |             REGUNEXUS CORE 6-TIER AI VERIFICATION            |
       +--------------------------------------------------------------+
                                      |
         +----------------------------+----------------------------+
         |                                                         |
         v [Administrative Verification]                           v [Pre-Clinical & SaMD Verification]
  +--------------------------------------+                  +--------------------------------------+
  | 1. Geocoding & Jaro-Winkler Address  |                  | 4. Bilingual Cosine Semantic Mapper |
  |    Reconciler Engine                 |                  |    and Medical NLP Lexicon Bridge    |
  +--------------------------------------+                  +--------------------------------------+
         |                                                         |
         v                                                         v
  +--------------------------------------+                  +--------------------------------------+
  | 2. SaMD Continuous Learning Risk     |                  | 5. DAG-Based Structural Dependency   |
  |    Heatmap & Version Trace Engine    |                  |    and Compliance Change Forecaster  |
  +--------------------------------------+                  +--------------------------------------+
         |                                                         |
         v                                                         v
  +--------------------------------------+                  +--------------------------------------+
  | 3. Cross-Dataset Covariance          |                  | 6. Pre-Clinical Waveform, Anomaly &  |
  |    Data Leakage Frobenius Detector   |                  |    Benford-KS Authenticity Audit Loop|
  +--------------------------------------+                  +--------------------------------------+
5.1 WOW AI Feature 1: Multi-Agent Discrepancy Reconciliation Engine
Clinical & Technical Context
Medical device manufacturers often list varied address representations across Certificate of Free Sale (CFS), Quality System certificates, and local applications. For example, Suite 100, 1200 Innovation Parkway vs STE 100, 1200 Innovation Hwy can trigger immediate administrative hold patterns under strict regulatory review. This engine automatically reconciles formatting variations.
Mathematical Distance Protocols
The engine evaluates address strings using three complementary calculation steps:
Jaro-Winkler Distance (String Similarity):
Calculates similarities between address string elements:

Where Jaro string distance 
 is determined by:

and:
 matches characters within distance limit 
.
 represents transposition counts.
 is the matching prefix length (up to 4 characters).
 is a scaling constant (default set to 
).
Normalized Levenshtein String Match Penalty:
Evaluates character insertion and deletion differences across strings:

Where 
 is:
Geographic Proximity via Haversine Distance:
When string match similarity falls between 
 and 
, the engine triggers a geocoding check to resolve the coordinates (Latitude 
, Longitude 
) for each address. It then computes the distance over the Earth's surface:

Using 
:
If 
, the system flags the address as a Minor Format Variation (e.g., Suite 100 vs STE 100) and marks the check as passed.
If 
, it reports a Critical Address Mismatch, highlighting the conflicting values on the review board.
5.2 WOW AI Feature 2: Automated Adaptive-vs-Locked Algorithm Audit Matrix
Clinical & Technical Context
Continuous-learning (adaptive) AI diagnostics run risks of model drift or unexpected shifts in performance once deployed. ReguNexus scans pre-clinical documentation to classify the model's design framework and verify that required quality control protocols are present.
Classification Pipeline & Decision Trees
Behavior Profiling: Scans design assets and user manuals for active terms indicating runtime updates (e.g., "online model updates", "continuous training", "real-time weight adjustments").
Version Logic Audit: Verifies model version rules. Standard locked models expect strict semantic versioning (
). If the software uses epoch markings or is deployed without traditional version splits, the system raises warnings.
Protocol Check: If adaptive features are identified, the system searches the dossier for a Post-Market Performance Monitoring and Verification Protocol (上市後性能監測與驗證機制). If missing, it generates an administrative objection referencing TFDA and IEC 62304 standards.
5.3 WOW AI Feature 3: Deep Cross-Dataset Data Contamination Detector
Clinical & Technical Context
Evaluating clinical AI systems requires complete isolation between training and testing cohorts. Overlap anomalies misrepresent accuracy metrics, introducing clinical risks once software is implemented.
Contamination Analysis Logic
The detector processes diagnostic logs and dataset splits using three check patterns:
Patient Identifier Overlap:
Compares patient identifier hashes (
 and 
) to detect direct cohort reuse:

Any ratio greater than 
 triggers a critical alert.
Covariance Feature Space Drift:
Detects deep, hidden duplication (like multiple slices from the same CT volume being split across training and test sets) by measuring covariance similarities using the Frobenius norm:

If the coordinate offset 
 falls below a minor threshold 
, the system flags a Dataset Contamination Risk indicating identical underlying biometric profiles.
Detection Report Triggers:
Red flags are raised if validation logs exhibit over-indexing or mismatching feature spaces. The agent flags the affected table and automatically drafts a corrective finding in the review report, directing developers to isolate demographic data groups.
5.4 WOW AI Feature 4: Bilingual Term Semantic Mapping Engine (NEW)
System Purpose & Clinical Utility
Medical device applications are frequently translated across English and traditional Chinese regulatory domains. Minor shifts in translation can result in mismatching administrative classes or functional errors (e.g., translating "reprocessing" to generic "重複製造" instead of the required "重處理效能確效"). This engine automatically maps bilingual terms against verified TFDA dictionary terms.
code
Code
+-----------------------------------------------------------------------------------------+
|                  Bilingual Semantic Mapping & Alignment Pipeline                        |
+-----------------------------------------------------------------------------------------+
  [Source Submission Term]                                    [Official TFDA Directory]
            |                                                             |
            v [Embeddings Generator]                                      v [Embeddings Generator]
  [Vector Representation u]                                   [Vector Representation v]
            \                                                             /
             \___________________________   _____________________________/
                                         \ /
                                          v [Cosine Similarity Calculation]
                             CosSim(u, v) = (u . v) / (||u|| ||v||)
                                          |
                        Does similarity exceed threshold (0.88)?
                                /                  \
                               / Yes                \ No
                              v                      v
                       [Verify Translation]   [FLAG EXCEPTION]
                                              Suggest Taiwanese standard terms
Vector Space Projection & Cosine Mapping Formulation
The engine projects extracted terms into high-dimensional embedding spaces, calculating alignment matching via Cosine Similarity:

Where:
 is the vector of the translated term extracted from user materials.
 is the target vector representation of verified Taiwanese TFDA standards.
If 
, the system concludes the term matches regulatory standards.
If 
, it highlights the mismatch and recommends standard Taiwanese medical vocabulary to align the submission.
5.5 WOW AI Feature 5: DAG-Based Structural Dependency Audit Map (NEW)
System Purpose & Clinical Utility
Complex medical submissions are highly interdependent; altering a software version code in Section 1.1 can invalidate clinical tests in Section 8.7 or Quality System documents in Section 5.3. By representing submission sections as a Directed Acyclic Graph (DAG), the platform traces these relationships and projects risk factors downstream whenever elements are changed.
code
Code
+-------------------------------------------------------------+
       |             Directed Acyclic Graph (DAG) Structure           |
       +-------------------------------------------------------------+
                                     |
                                     v
                       +-----------------------------+
                       | Sec 1.1: Software v3.2 Code |
                       +-----------------------------+
                                /           \
                               /             \
                              v               v
               +-----------------------+     +-----------------------+
               |  Sec 5.3: QSD Scope   |     | Sec 7.5: User Manual  |
               +-----------------------+     +-----------------------+
                                \             /
                                 \           /
                                  v         v
                       +-----------------------------+
                       | Sec 8.7: Software Check-set |
                       +-----------------------------+
Graph Formulations & Centrality Metrics
We define the submission dependency graph as 
, where 
 represents regulatory checkpoints and 
 is their directed dependency relationships. To assess the impact of changes, the system calculates the system centrality metrics of affected nodes:

Where:
 is the adjacency matrix representing node relationships, where 
 if node 
 directly influences node 
.
 is the principal eigenvalue.
High centrality scores identify critical documentation nodes. If a change is made to a high-centrality element, the platform flags the impact downstream, prompting the reviewer to verify linked test cases.
5.6 WOW AI Feature 6: Pre-Clinical Technical Report Authenticity & Noise Audit Loop (NEW)
System Purpose & Clinical Utility
To protect patient safety, pre-clinical testing results (such as electromagnetic compatibility reports or software validation datasets) must be fully authenticated before submission. This engine scans datasets to identify potential red flags, copy-paste errors, or synthetically generated data anomalies.
code
Code
+---------------------------------------------------------------------------------+
|                       Pre-Clinical Authenticity Verification                    |
+---------------------------------------------------------------------------------+
  [Input Dataset Logs/Metrics]
                |
                v
  [1. Track Lead Digit Distributions (1 to 9)] -> Mapped to Benford's Expectation Curve
                |
                v
  [2. Kolmogorov-Smirnov Statistical Assessment]
                |
                | Calculates drift: D = sup | F_n(x) - F_0(x) |
                v
  Is calculated drift D greater than acceptable limits?
          /                       \
         / Yes                     \ No
        v                           v
  [FLAG POTENTIAL ANOMALY]     [Confirm Natural Dispersion]
  Synthetically generated      (Passed Authenticity Verification)
  data detected
Benford's Law and Kolmogorov-Smirnov Statistical Audit
Natural physical testing values (like leakage currents or signal decay logs) are expected to display natural numerical distributions. To verify authenticity, the system evaluates lead digit distributions against Benford's Law expectations:

The system then runs a Kolmogorov-Smirnov (K-S) statistical test to evaluate calculated variations 
 against expected distributions 
:

Where:
 is the cumulative empirical distribution of lead digits.
 is the cumulative distribution expected under Benford's Law.
If calculated drift 
 exceeds the alpha critical value 
, the system flags potential authenticity anomalies. This helps reviewers identify fabricated testing logs or duplicated noise profiles.
6. Human-in-the-Loop Interactive Review & Persistency Architectures
The platform keeps the human reviewer central to the process, allowing them to verify or correct automated compliance evaluations.
6.1 Three-State Interactive Review Switch
Pass (綠色/合規): Confirm and sign off on verified compliance checkpoints.
Fail (紅色/不符): Mark a section as deficient. The system auto-populates the feedback box with standard TFDA regulatory objection phrasing to speed up drafting.
N/A (灰色/免除): Skip checks that are not applicable to the device under review (e.g., omitting sterile process checks for a non-sterile active instrument).
code
Code
+-------------------------------------------------------------------------------+
| TFDA Checklist Card [Clause 1-6]                                              |
| "Verify manufacturing site designations and address formats across registries" |
|                                                                               |
| [ PASS: Compliance ]  [ FAIL: Deficiencies* ]  [ N/A: Exclude ]               |
|                                                                               |
| Reviewer Notes & Comments:                                                    |
| [ Jaro-Winkler score identifies minor STE/Suite discrepancies.               ] |
| [ Recommend align addresses across CFS and local registries.                 ] |
+-------------------------------------------------------------------------------+
6.2 Workspace Persistent Storage Loop
User edits, status changes, and review notes are saved immediately in localStorage. Debounced caching write states to local storage to prevent data loss from accidental browser reloads or network drops.
7. Specification of the 6 WOW Visualization Engines (Recharts-Ready)
To maintain the Editorial Aesthetic, charts feature clean geometries, minimal grids, and high-contrast styling, avoiding typical multi-colored dashboard elements.
code
Code
+---------------------------------------------------------------------------------------------------+
|                           REGUNEXUS 6-PANEL HIGH-CONTRAST METRIC BOARD                            |
+---------------------------------------------------------------------------------------------------+
|  [ Panel G1: Completed Steps Rings ] |  [ Panel G2: Address Distance Column ] |  [ Panel G3: Scatter Matrix ]     |
|                                      |                                        |                                   |
|               ( @@ )                 |                 |     |                |              *  o                 |
|               (  )                   |                 |     |                |             o   *                 |
|                                      |                                        |                                   |
|  Tracks overall progress across the  |  Displays similarity scores paired     |  Plots feature correlations;      |
|  8 main administrative sections.     |  with calculated geographic distance.  |  overlaps are marked in deep red. |
+--------------------------------------+----------------------------------------+-----------------------------------+
|  [ Panel G4: 3x3 Heatmap Grid ]      |  [ Panel G5: Section Area Coverage ]   |  [ Panel G6: Spiderweb Radar ]    |
|                                      |                                        |                                   |
|              [■][ ][ ]               |                / \                     |                 /\                |
|              [ ][■][ ]               |               /   \_                   |                /  \               |
|              [ ][ ][ ]               |              /      \                  |                \  /               |
|                                      |                                        |                 \/                |
|  Identifies potential compliance     |  Displays review coverage progress     |  Evaluates overall dossier        |
|  risks in continuous AI systems.     |  across the 8 regulatory chapters.     |  completeness before submission.  |
+---------------------------------------------------------------------------------------------------+
7.1 Graph 1: Agenda Compliance & Clause Audit Donut Chart
Purpose: Tracks global, high-level audit completion.
Type: Concentric split-ring doughnut chart.
Implementation Parameters:
code
JSON
[
  { "name": "Passed Steps", "value": 45, "fill": "#14B8A6" },
  { "name": "Deficiencies", "value": 8, "fill": "#E11D48" },
  { "name": "N/A Exempt", "value": 5, "fill": "#64748B" },
  { "name": "Pending Review", "value": 12, "fill": "#D97706" }
]
Visual Details: Thin structural rings with interactive hover thickness adjustments.
7.2 Graph 2: Cross-Document Address Distance Matrix Bar Chart
Purpose: Visualizes manufacturer address discrepancies.
Type: Dual Y-axis clustered column chart.
Implementation Parameters:
code
JSON
[
  { "doc": "FSC (製售)", "jaroSimilarity": 1.00, "distance_m": 0 },
  { "doc": "QSD Cert", "jaroSimilarity": 0.82, "distance_m": 4.1 },
  { "doc": "Labeling", "jaroSimilarity": 0.74, "distance_m": 12.8 },
  { "doc": "Application Form", "jaroSimilarity": 0.94, "distance_m": 0.2 }
]
Visual Details: Bars represent Jaro-Winkler similarities against physical geocoding distances, highlighting warning thresholds.
7.3 Graph 3: Training-to-Test Set Covariance Joint Scatter Plot
Purpose: Displays data contamination anomalies in machine-learning models.
Type: Quadrant dispersion scatter plot.
Implementation Parameters:
code
JSON
[
  { "train_cov": 0.825, "test_cov": 0.824, "flag": "contam_leak" },
  { "train_cov": 0.441, "test_cov": 0.441, "flag": "contam_leak" },
  { "train_cov": 0.961, "test_cov": 0.960, "flag": "contam_leak" },
  { "train_cov": 0.224, "test_cov": 0.224, "flag": "contam_leak" }
]
Visual Details: Plots covariance values directly; highly correlated coordinates near the diagonal indicate potential dataset leaks.
7.4 Graph 4: SaMD Continuous-Learning Risk Matrix Heatmap
Purpose: Highlights potential compliance risks in adaptive AI algorithms.
Type: 3x3 Heatmap matrix using custom SVG nodes.
Implementation Parameters:
code
JSON
[
  { "adaptivity": "Locked", "monitoring": "Full Protocol", "risk": 1, "color": "#14B8A6" },
  { "adaptivity": "Real-time updates", "monitoring": "None Provided", "risk": 9, "color": "#E11D48" },
  { "adaptivity": "Planned updates", "monitoring": "Basic Checks", "risk": 5, "color": "#F59E0B" }
]
Visual Details: Grid nodes are styled based on risk levels. Clicking a cell updates review notes with applicable mitigation advice.
7.5 Graph 5: TFDA Chapter Audit Coverage Area Chart
Purpose: Displays review coverage across the 8 main regulatory chapters.
Type: Layered area chart.
Implementation Parameters:
code
JSON
[
  { "chapter": "Ch.1", "completeness": 100 },
  { "chapter": "Ch.2", "completeness": 80 },
  { "chapter": "Ch.5", "completeness": 94 },
  { "chapter": "Ch.8", "completeness": 44 }
]
Visual Details: Clean, semi-transparent layered area paths built on a muted background grid.
7.6 Graph 6: Review Readiness & Material Integrity Radar Chart
Purpose: Evaluates overall dossier completeness before submission.
Type: Multi-axis path spider-web radar chart.
Implementation Parameters:
code
JSON
[
  { "category": "Administrative Consistency", "score": 95 },
  { "category": "QMS Registries", "score": 88 },
  { "category": "SaMD Cybersecurity Reports", "score": 40 },
  { "category": "Pre-Clinical Evidence", "score": 75 },
  { "category": "Safety Assays", "score": 90 }
]
Visual Details: An elegant, high-contrast polygonal outline over thin circular radar grids.
8. Document Export & External Workspace Integrations
Converting findings into formal reporting documents is a critical step in regulatory evaluations.
code
Code
[ Checked Dossier State ]
                                          |
                        +-----------------+-----------------+
                        |                                   |
                        v                                   v
             [ Google Auth Popup ]                [ Local Format Builder ]
                        |                                   |
                        v [Identity Token]                  +---> Raw Markdown (.md)
            [ Google Docs API Payload ]                     |
                        |                                   +---> Styled HTML (.html)
                        v
        [ Sync styled cloud document ]
8.1 Google Docs Cloud Integration Flow
The cloud export flow operates securely without local credentials storage:
OAuth Setup & Token Management:
The system checks if active scopes exist. If missing, it activates set_up_oauth.
Displays the Google sign-in component with standard Google branding and styles.
Access tokens are cached in volatile RAM state vectors to protect user credentials.
code
TypeScript
// Minimum Required Google Workspace API scopes
const GOOGLE_AUTH_SCOPES = [
  'https://www.googleapis.com/auth/documents', // Read and write Docs files
  'https://www.googleapis.com/auth/drive.file' // Manage specific app files
];
Cloud Document Assembly:
Generates formatted documents using the Google Docs API.
Compiles findings into standard templates using clean styles and font formats.
Outputs structured deficiency reports, complete with table matrices and action guidelines.
code
TypeScript
// Google Docs API Payload Assembly
const docGenerationPayload = {
  title: "TFDA PRE-MARKET REGULATORY DEFICIENCY OBJECTIONS REPORT",
  requests: [
    { insertText: { text: "TFDA Pre-Market Technical Audit Statement\n", location: { index: 1 } } },
    { updateParagraphStyle: { range: { startIndex: 1, endIndex: 43 }, paragraphStyle: { headingId: "HEADING_1" } } }
  ]
};
8.2 Local Material Packaging
Well-Formatted Markdown (.md): Generates clean, reader-accessible compliance reports, perfect for git-based tracking.
Print-Ready HTML Pages (.html): Compiles findings into single-page documents with inline CSS, ideal for local distribution or printing.
9. Security, Data Privacy & Sandbox Protections
9.1 Data Isolation Rules
In-Memory Buffering: Uploaded files (PDFs, JSONs, Markdowns) are processed as volatile in-memory buffers and are not written to long-term storage caches.
Key Security: The Gemini API key remains hosted inside server-side environments on Cloud Run. No API secrets are ever exposed to client frameworks.
Redaction Controls: High-performance algorithms scan submissions to identify and redact personal health information (PHI) before document processing begins.
10. Technical Project Timeline
code
Code
========================================================================
Phase 1: Inflow Pipelines & Normalization (Weeks 1-2)
- Configure Express backend file streaming with 50MB payload supports.
- Build structural tokenizers for custom skill.md guidelines.
- Establish the Editorial Aesthetic layout framework.

Phase 2: Core Analytical Engines (Weeks 3-4)
- Integrate Gemini client API schemas.
- Implement geocoding checks and Frobenius covariance detectors.
- Connect status switch registries to interactive check card interfaces.

Phase 3: Graphical Panels & UI Dashboards (Weeks 5-6)
- Build real-time neural visualizers and log trace displays.
- Assemble the 6 custom Recharts compliance charts.
- Set up local persistency using localStorage.

Phase 4: Cloud document synchrony & Delivery (Weeks 7-8)
- Integrate secure Google Auth popup models.
- Build document assembly modules for the Google Docs API.
- Validate security regulations and deployment configurations.
========================================================================
11. Concluding Follow-Up Questions (Exactly 20 Items)
Please review the following design and technical questions to help finalize development:
Scanned PDF Processing: For scanned or non-readable PDF dossiers, should we integrate an OCR pipeline (like Google Cloud Vision or Tesseract) directly on our Express backend?
Pre-Clinical Checklist Scope: Should we expand the default skill.md checks to cover international classifications, such as European CE (MDR) or US FDA 510(k), or maintain a strict TFDA focus?
Statistical Limits: What threshold levels should the Data Contamination module use for the Jaro-Winkler address check (
) and the Frobenius covariance check (
)?
Google Docs Templates: For Google Docs exports, should the system construct documents using a preloaded organization template or create standard minimalist formats?
Parallel Analysis Runs: Do we want to process the entire 8-section compliance audit in a single high-context API call, or split the work into separate parallel agent runs for each chapter?
Bilingual Translation Support: Should the translation mapping engine support automatic terminology conversion for other source languages (e.g., German or Japanese technical files) into traditional Chinese?
Maps Verification Keys: Will we integrate live Google Maps Platform API keys for spatial calculations, or are offline geocoding utilities sufficient?
Dossier Size Limits: What is the maximum expected file size for uploads? Large clinical attachments can exceed 200MB and may require stream-based storage configurations.
Cybersecurity Standards: Under Chapter 8-6, do you want to audit security reports against specific external standards (e.g. UL 2900, IMDRF Guidelines) or TFDA-specific directives?
Multi-User Collaboration: Should we add real-time collaborative database storage (like Firestore) to allow audit teams to work on the same dossier at the same time?
Immutable Audit Trails: Does your organization require immutable audit logs (like custom CSV log trackers) record reviewer decisions and changes to checked states?
Automatic PHI Scrubbing: Should we run automated preprocessing filters to redact patient names and biometric identifiers before data is sent to the Gemini API?
Custom Model Adaptations: Will the app require connection to custom models trained on specific regulatory datasets, or are standard Gemini models sufficient for analysis?
Custom Checklist Design: Should users be able to dynamically modify, delete, or add custom regulatory clauses within the UI dashboard, or should they be managed purely through modifications in the uploaded skill.md file?
Offline Working Support: Does the application require offline access, letting users log comments and review checklist items without an active network connection?
AI Rationale Disclosures: For critical engineering validations, should the AI output step-by-step technical explanations justifying its compliance determinations?
Dynamic Interactive Visuals: Do you want live log terminal lines to be clickable, immediately navigating the user to the corresponding checklist card?
Documents Theme Styles: Should exported documents support custom corporate styles (including logos, custom headers, and cover pages) before exporting to PDF or Google Docs?
Conflict Resolver Rules: How should the system flag and handle situations where a reviewer's manually entered note contradicts the automated finding from the AI analysis engine?
Auditing Role Clearances: Do we need to implement user roles with custom clearance permissions (e.g. Lead Reviewer, Technical Specialist, Officer) to control editing access to specific dossier chapters?
