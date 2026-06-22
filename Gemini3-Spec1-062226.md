TECHNICAL SPECIFICATION DOCUMENT
MULTI-AGENT premarket 510(K) REGULATORY REVIEW AND VERIFICATION PLATFORM
Document Version: 4.2.0-PRO
Author: Principal Software Architect & Lead Regulatory Expert AI System
System Class: Software as a Medical Device (SaMD) Compliance Auditing and Discrepancy Engine
Regulatory Target: Taiwan Food and Drug Administration (TFDA) Pre-market Notification & Standard US FDA 510(k) Submissions
1. EXECUTIVE SUMMARY & SYSTEM SCOPE
In the domain of medical device regulatory affairs, the process of drafting, compiling, and auditing a 510(k) Technical Registration Dossier or a Taiwan Food and Drug Administration (TFDA) pre-market approval application is notoriously complex, highly iterative, and prone to catastrophic technical mismatches. Submissions often consist of thousands of pages of unstructured data across multiple certificates: Free Sale Certificates (CFSM), Letters of Authorization (LoA), Quality Management System certificates (QMS/QSD), Clinical Validation Reports, and Software Specifications. A single typographical mismatch in a manufacturer's factory address (e.g., "Suite 400" versus "STE 400" or an incorrect zip code) or an obscure software weight variable in an Artificial Intelligence/Machine Learning (AI/ML) algorithm can trigger a regulatory rejection, prompting a "Deficiency Letter" or "Major Deficiency" holding pattern, adding months to clinical adoption timelines.
The 510(k) Medical Device Regulatory Review Agent is a full-stack, AI-driven pre-market auditing workspace designed to ingest, process, verify, and reconcile complex medical device registration dossiers. Utilizing an advanced, multi-tiered AI agent pipeline powered by the server-side @google/genai SDK and structured JSON response models, the system ingests raw dossier text or structured JSON data, and parses them against me-made statutory checkbooks (anchored in Taiwan's 醫療器材許可證核發與登錄準則 / Medical Device Registration and Licensing Regulations).
The platform's user interface is built on React 18 and Vite, implementing the "Professional Polish" Slate-Contrast Design Theme. This theme optimizes information density, cognitive scanning speed, and user focus, using high-contrast slate grids, clear navigation rails, micro-interactive SVG reporting graphs, a nested regulatory workbook, an interactive LLM-driven consultation copilot, and an automated deficiency letter compiler. It integrates deep statistical compliance auditing—such as detecting data contamination leakage in clinical test cohorts and flagging continuous learning parameters in adaptive online neural-network classifiers. This document outlines the exhaustive technical specifications of this system, mapping every CSS declaration, state flow, database model, visualization vector, API routing pathway, and advanced AI agent strategy.
2. USER INTERFACE LAYOUT & CSS CLASS SPECIFICATIONS
The visual hierarchy of the platform is engineered around the Professional Polish framework. It establishes a structural, desktop-first container pattern optimized for a standard dual-screen medical auditor workstation (minimum design target 1024px width, scaling up to ultra-wide 4K monitors with viewport fluid constraints). It prioritizes clean light backgrounds (bg-slate-50), structured lines (border-slate-200), dark contrasting slate text elements (text-slate-800), deep indigo brand cues (bg-indigo-600), and clean emerald status highlights (text-emerald-700).
code
Code
+----------------------------------------------------------------------------------------------------+
|                                      HEADER BAR (h-14, white)                                      |
|  [Logo & Badge]                                                  [Model Config] [Auditing Button]  |
+----------------------------------------------------------------------------------------------------+
|                                  MAIN WORKSPACE FRAME (h-[calc(100vh-5.5rem)])                     |
| +-------------------------+ +---------------------------------------+ +--------------------------+ |
| |                         | |                                       | |                          | |
| |  PANEL 1: DOSSIER       | |  PANEL 2: ACTIVE RECONCILIATION       | |  PANEL 3: INTELLIGENCE   | |
| |  INPUT PANEL            | |  WORKBOOK (Scrollable Area)           | |  DASHBOARD & CHAT        | |
| |                         | |                                       | |                          | |
| |  - Drag & Drop Loader   | |  - Active Chapters (Accordion-based)  | |  - 6 Compliance Graphs   | |
| |  - Markdown Dossier Tx  | |  - Override Actions (Pass/Fail/NA)    | |  - Regulatory Copilot    | |
| |  - Audit Skill Config   | |  - Harmonizer & Explanatory Alerts    | |    Consultation Engine   | |
| |  - Telemetry Logs       | |  - Deficiency Letter Board            | |  - Next Steps Buttons    | |
| |                         | |                                       | |                          | |
| |  [w-72, bg-white, Scroll]  | [Flex-1, bg-slate-50, Overflow-Y]       | |  [w-80, bg-white, Scroll] | |
| +-------------------------+ +---------------------------------------+ +--------------------------+ |
+----------------------------------------------------------------------------------------------------+
|                                    ACCORDION PANEL (Follow-Up Questions)                           |
+----------------------------------------------------------------------------------------------------+
|                                      STATUS FOOTER (h-8, Slate-800)                                |
|  [Module Details]                                                   [Port & Engine Operational]    |
+----------------------------------------------------------------------------------------------------+
2.1 The Global Structural Elements
Header Navigation Bar (h-14):
CSS Classes: h-14 bg-white border-b border-slate-200 px-6 flex items-center justify-between shrink-0 sticky top-0 z-30 shadow-xs.
Attributes: Anchors the application context. Contains the vector shield check icon ShieldCheck (styled with p-1.5 bg-indigo-50 text-indigo-600 rounded), the application brand (text-sm font-black tracking-tight text-slate-800 uppercase), and the dynamic toolbelt that wraps the computational model dropdown (bg-slate-50 text-slate-700 font-mono text-[10px] font-bold py-1 px-2 rounded border border-slate-200) and the high-contrast trigger button (bg-indigo-600 hover:bg-indigo-700 text-white shadow-xs cursor-pointer active:scale-95 duration-100).
Left Panel: Input & Control Sidebar (w-72):
CSS Classes: w-full md:w-72 bg-white border-r border-slate-200 p-4 flex flex-col gap-4 overflow-y-auto shrink-0.
Attributes: Holds dossier load state. Highlights include the preset loader button (w-full bg-slate-50 border border-slate-200 hover:bg-slate-100 hover:border-slate-300 text-slate-700 text-[10px] font-bold py-2 px-3 rounded-lg transition) and the drag-and-drop landing target (dashed slate borders border-2 border-dashed border-slate-200 rounded-lg p-3 bg-slate-50 text-center select-none). Inside, a dedicated monospaced log screen (bg-slate-900 border border-slate-950 text-emerald-400 rounded-lg p-3 h-40 max-h-40 overflow-hidden font-mono text-[9px] leading-relaxed) is mounted at the bottom, capturing the agent's real-time reasoning logs in memory.
Center Panel: Auditing Workbook Table (flex-1):
CSS Classes: flex-1 flex flex-col bg-slate-50 overflow-hidden.
Attributes: Houses the active auditing worksheet inside a scrollable content box. The workbook's control panel uses an offline filtering toolbelt (bg-white border-b border-slate-200 p-3 flex flex-wrap items-center justify-between gap-3 shrink-0) supporting dropdown routing based on statutory chapters, quick button filters based on evaluation status (Pass, Fail, Pending, N/A), and an text keyword filter box with a search icon overlay.
Right Panel: Intelligence Dashboard & Copilot Chat (w-80):
CSS Classes: w-full md:w-80 bg-white border-l border-slate-200 p-4 flex flex-col gap-4 overflow-y-auto shrink-0 shadow-inner.
Attributes: Provides the analytical layer. The top segment hosts the 6 visual graphs configured within a light-grey card with sharp borders (bg-white rounded-xl border border-slate-250 p-4 shadow-sm). The lower half dynamically displays the chat interface (flex-1 bg-white rounded-xl border border-slate-200 shadow-sm overflow-hidden min-h-[300px] flex flex-col).
20 Follow-Up Questions Dock (Bottom):
CSS Classes: bg-slate-50 border-t border-slate-200 px-6 py-4 shrink-0.
Attributes: Expands at the viewport footer to list categorical statutory questions, rendered in a 4-column balanced grid layout (grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4).
System Status Bar Footer (h-8):
CSS Classes: h-8 bg-slate-800 border-t border-slate-700 flex items-center justify-between px-6 text-white text-[10px] shrink-0 font-mono.
Attributes: Outputs diagnostic metadata (PORT: 3000, STATUS: LIVE, SYSTEMS OPERATIONAL) to maintain professional "technical utility" without cluttering the main operational workspace.
3. COMPLEX DATA MODEL & STATE SCHEMA
Data flow in the platform is managed via structured states using TypeScript to ensure strong typing. It bridges unstructured dossier material (the pre-market file input) with highly structured statutory checklists and AI-driven telemetry data.
code
Code
[ Unstructured Dossier Content (materials state) ]
                                              |
                                              v
                                  [ Execute Scan API Post ]
                                              |
                                              v
                              [ Structued JSON Schema Output ]
                                              |
                                              +----> Set 'analysisResult' State (AnalysisResult)
                                              |
                                              v
                             [ Map suggested_status to Checklist ]
                                              |
                                              +----> Set 'reviewStates' (ReviewStates)
                                                              |
                                                              v
                                          [ User Manual Overrides & Note Edits ]
                                                              |
                                                              v
                                              [ Live Re-Compilation UI Updates ]
3.1 Type Definitions (src/types.ts)
The entire application relies on the following schema definitions inside src/types.ts:
code
TypeScript
export interface ChecklistItem {
  id: string;      // Unique checkpoint code (e.g., '1-1', '8-7')
  text: string;    // Raw statutory text
  note?: string;   // Regulatory guidance or advisory note
}

export interface ChecklistSection {
  id: string;      // Section primary key (e.g., 'sec1', 'sec8')
  title: string;   // Chapter Title
  items: ChecklistItem[];
}

export interface ReviewState {
  status: "pass" | "fail" | "na" | "pending";
  note: string;    // Human auditor or AI-written findings detail
}

export interface ReviewStates {
  [key: string]: ReviewState; // Map clause ID to state
}

export interface AnalysisResult {
  scorecard: {
    total_passed: number;
    total_failed: number;
    total_na: number;
    overall_compliance_score: number;
  };
  discrepancy_matching_feature: {
    mismatch_severity: "High" | "Medium" | "Low" | "None";
    matrix: Array<{
      field: string;               // Target verification field (e.g., Factory Name, Address)
      app_form: boolean | string;   // Entry in registration form
      cfsm: boolean | string;       // Entry in Free Sale Certificate (CFSM)
      loa: boolean | string;        // Entry in Letter of Authorization
      qms: boolean | string;        // Entry in Quality Management certificate
      status: "Matched" | "Mismatched" | "Not Sourced";
      match_confidence: number;     // Statistical confidence percentage (0 to 1)
      findings: string;             // Analytical finding explaining comparison
    }>;
    entity_reconciliation_summary: string;
  };
  adaptive_vs_locked_matrix_feature: {
    algorithm_type: "Adaptive" | "Locked" | "Undetermined";
    detected_indicators: string[]; // Indicators present (e.g., 'backpropagation', 'optimization switch')
    post_market_protocol_found: boolean;
    deficiency_notice_draft: string; // Statutory text for deficiency letter
    risk_rating: "High" | "Medium" | "Low" | "Critical";
  };
  data_contamination_detector_feature: {
    train_test_isolated: boolean;
    overlapping_cohorts: string[];  // List of overlapping cohorts or records found
    contamination_severity: "Critical" | "High" | "Medium" | "None";
    similarity_score_percentage: number; // Quantitative measure of overlap
    technical_noncompliance_alert_text: string;
  };
  chapters_compliance: Array<{
    chapter_id: string;             // References ChecklistSection ID
    readiness_percentage: number;
    summary: string;
    items: Array<{
      item_id: string;              // References ChecklistItem ID
      suggested_status: "pass" | "fail" | "na";
      findings_detail: string;
      regulatory_gap_detail: string;
      prescriptive_fix_action_plan: string;
    }>;
  }>;
  ai_live_execution_log: string[]; // Detailed trace logs populated step-by-step
}
3.2 State Flow and React Hook Synchronization
The states defined in App.tsx coordinate the workbook interface:
materials State (String):
Stores the currently processed dossier raw text. Binds to the left panel textarea.
activeSkillMd State (String):
Stores the operating instructions, serving as the system's "regulatory brain" (DEFAULT_SKILL_MD). Can be expanded and loaded in full text.
analysisResult State (AnalysisResult | null):
Initialized to null. On executing a scan, the Express route /api/review returns a fully populated compliance payload satisfying the AnalysisResult schema. Setting this state triggers three effects:
Unveils the detailed alerts in the workbook stream.
Animates the progress bars, radial rings, Venn diagrams, and heatmap grids inside ReviewCharts.
Pre-populates the interactive workbook overrides.
reviewStates State (ReviewStates):
Serves as the editable database. When the active scan completes, it iterates through chapters_compliance items, projecting their suggested_status and analytical findings directly into the specific clause state keys. The auditor can override any clause status manually via button clicks, or edit paragraph notes directly. All graphs and overall metrics update in real-time based on these user-edited overrides.
chatPrepopulationText State (String):
Bridges the suggested actions and follow-up links to the conversational agent. Clicking any suggestion transfers the prompt directly into the input container, focusing the cursor and triggering the AI execution flow.
4. DEEP DIVE: THE 6 COMPLIANCE MATRIX VISUALIZATIONS
The right-hand intelligence sidebar features six high-fidelity compliance metrics. In compliance with regulatory visualization guidelines, these charts rely on native CSS vectors and inline responsive layout structures to ensure they render reliably within sandboxed browser environments without requiring heavy, unstable external libraries.
code
Code
+-----------------------------------+-----------------------------------+
|  1. Compliance Index (Radial circle) |  2. Chapter Profile (Spoke bars)  |
|                                   |                                   |
|             ( 72% )               |  SEC1: |======------| (45%)       |
|                                   |  SEC2: |=========---| (78%)       |
+-----------------------------------+-----------------------------------+
|  3. Entity Matrix (Match Heatmap) |  4. Algorithm Risk (Flow Signal)  |
|                                   |                                   |
|      Fld  App  CFS  LoA  QMS      |    [ Adaptive ] ===> Continuous   |
|     Name   V    V    X    V       |         *Active Drift Signal*     |
+-----------------------------------+-----------------------------------+
|  5. Leakage Isolation (Venn-Diag.)|  6. Extraction Latency (Progress)  |
|                                   |                                   |
|        ( Train (Leak) Test )      |   |========------|                |
|             18.4% Leaked          |   Speed: 132 ms / checklist item  |
+-----------------------------------+-----------------------------------+
4.1 Graph 1: Overall Compliance Score Radial Circle
Technical Metric Represented: Combined pass rate of checklist items. Compares (Pass + N/A) / (Pass + Fail + N/A) as a percentage.
Component Architecture: Inline HTML SVG utilizing strokeDasharray math to draw circular paths.
Implementation Blueprint:
code
Tsx
<svg viewBox="0 0 36 36" className="w-full h-full transform -rotate-90">
  <circle
    cx="18" cy="18" r="15.915"
    fill="transparent" stroke="#E2E8F0" strokeWidth="3.5"
  />
  <circle
    cx="18" cy="18" r="15.915"
    fill="transparent" 
    stroke={computedComplianceScore >= 80 ? "#10b981" : computedComplianceScore >= 60 ? "#f59e0b" : "#f43f5e"} 
    strokeWidth="3.5"
    strokeDasharray={`${computedComplianceScore}, 100`}
    className="transition-all duration-1000 ease-out"
  />
</svg>
Dynamic Behavior: Smoothly transitions between scores using CSS transitions. The stroke color changes from crimson red (#f43f5e, 
) to warning gold (#f59e0b, 
) to clinical green (#10b981, 
) based on real-time checklist audits.
4.2 Graph 2: Chapter Profile (Polar Spoke/Bar Representation)
Technical Metric Represented: Progression and readiness index across the eight statutory TFDA chapters.
Component Architecture: An auto-scrolling dashboard block containing stacked fluid bars.
Implementation Blueprint: Maps over chapterCompletenessList. It calculates the proportion of items in each chapter checked off as either "Pass" or "N/A" relative to the total number of items categorized in that segment, updating the width dynamically with Tailwind utility classes:
code
Tsx
<div style={{ width: `${ch.percentage}%` }} className="h-full bg-indigo-500 transition-all duration-500" />
Dynamic Behavior: Scales instantly during user overrides. Allows the auditor to quickly scan which of the eight regulatory chapters has outstanding gaps (e.g., administrative compliance vs. technical software verification).
4.3 Graph 3: Document Coverage & Entity Match Heatmap
Technical Metric Represented: Entity matching consistency. Compares registered firm names and addresses across the core verification forms.
Component Architecture: A highly optimized 
 cross-tabulation grid pane reflecting the discrepancy_matching_feature schema.
Implementation Blueprint: Outputs rows for "Factory Name" and "Factory Address", aligning cell status indicators side-by-side representing the Application Form, CFSM, LoA, and QMS databases. If a misalignment is flagged (e.g., "Suite 400" vs. "Unit 400" in the LoA), the cell background changes color, drawing attention to the specific field mismatch:
code
Tsx
const isMismatched = row.status === "Mismatched";
const cellStyle = isMismatched 
  ? "bg-rose-50 text-rose-700 border-rose-200" 
  : "bg-emerald-50 text-emerald-700 border-emerald-200";
Dynamic Behavior: Synthesizes mismatched characters (e.g., identifying spelling variances in "Acme Diagnostics Corp" vs. "Acme Biotech Inc.") and updates warning indicators in real-time.
4.4 Graph 4: Algorithm Risk State Fluid/Locked Inspector
Technical Metric Represented: Classification model safety. Audits whether the device runs a "Locked" parameter configuration or an "Adaptive" continuous learning algorithm.
Component Architecture: CSS layout visualization detailing state flows and warning indicators.
Implementation Blueprint: Displays a block containing a warning indicator that points to a loop diagram if the AI system flags continuous backpropagation elements in the technical specifications. If locked, it displays an static parameters validation signal.
Dynamic Behavior: Identifies phrases like "backpropagation", "weights update", or "dynamic telemetry training." Instantly flags these triggers to help auditors prevent unverified automated algorithm drift from bypassing regulatory review.
4.5 Graph 5: Data Contamination Venn Representation
Technical Metric Represented: Overlap ratio between the ML training dataset and the testing/validation patient dataset.
Component Architecture: Inline high-fidelity SVG path diagram plotting two overlapping responsive spheres.
Implementation Blueprint: Dynamically shifts circle overlap vectors based on the similarity score percentage. Features a highlighted crimson intersection representing the leaked patient records:
code
Tsx
<circle cx="43" cy="25" r="18" fill="#4f46e5" fillOpacity="0.25" stroke="#4f46e5" />
<circle cx="57" cy="25" r="18" fill="#ec4899" fillOpacity="0.25" stroke="#ec4899" />
{overlapPercent > 0 && (
  <path d="M 50 11 A 18 18 0 0 1 50 39 A 18 18 0 0 1 50 11 Z" fill="#ef4444" fillOpacity="0.6" />
)}
Dynamic Behavior: Instantly measures matching patient identifiers (e.g., indicating overlap between Boston-A6 training IDs and Boston-A6 validation subsets) and calculates the percentage variance.
4.6 Graph 6: Processing Latency Progress Bar
Technical Metric Represented: Quantitative measure of agent processing performance.
Component Architecture: Styled micro-progress layout panel.
Implementation Blueprint: Compares runtime computational metrics, displaying a progress bar that measures extraction time (expressed in milliseconds per checklist clause):
code
Tsx
<div className="absolute inset-y-0 left-0 bg-gradient-to-r from-indigo-500 to-indigo-400 w-3/4 animate-pulse" />
Dynamic Behavior: Measures model computation speed across gemini-3.1-flash-lite, gemini-3.5-flash, and gemini-3.1-pro-preview models, visually adjusting performance indicators based on model choice.
5. ARCHITECTURAL SPECIFICATION OF 3 NEW "WOW" AI FEATURES
To elevate this platform into an industry-leading regulatory suite, three additional WOW AI features are specified below. These address critical regulatory pain points in medical device registration, providing advanced, end-to-end automation that helps auditors identify compliance gaps and verify technical data.
code
Code
=============================================
                                 =         CUSTOM REGULATORY ENGINE          =
                                 =============================================
                                                       |
        +----------------------------------------------+----------------------------------------------+
        |                                              |                                              |
        v                                              v                                              v
[ WOW FEATURE A: Dynamic Translation & ]     [ WOW FEATURE B: Automated CyberSecurity ]     [ WOW FEATURE C: Multi-Institutional  ]
[ Address Entity Reconciliation Engine ]     [ SBOM & SaMD Threat Modeling Agent      ]     [ Clinical Cohort Overlap Detector    ]
        |                                              |                                              |
        +-- Compiles "Address Alignment Statement"     +-- Audits software configurations against     +-- Audits clinical validation records
        +-- Generates dual-language discrepancy maps   |   vulnerability databases (NVD)              |   matching demographic profiles
                                                       +-- Maps hardware/network specs to TFDA        +-- Cross-references patient IDs to detect
                                                           cybersecurity compliance requirements          mathematical validation sample leaks
5.1 WOW AI Feature A: Dynamic Translation & Address Entity Reconciliation Engine (行政地址對齊器)
1. Description and Regulatory Pain Point
When foreign medical manufacturers register Class II and Class III devices in international bureaus like Taiwan's TFDA, their documentation (LoAs, CFSMs, certificates) is often compiled by multiple agents in different countries. This leads to subtle address and naming inconsistencies that trigger regulatory rejections. For example, the Free Sale Certificate (CFSM) might display the manufacturer address as "STE 400, 100 Innovation Way, Boston", whereas the Quality Management System (QSD) certificate registers "Suite 400, 100 Innovation Way, Boston", and the Letter of Authorization (LoA) mistypes the zip code as "02110" instead of "02111".
Although these represent the identical manufacturing suite, standard pattern matchers flag these as mismatches, forcing human auditors to draft official queries. Feature A is an AI-powered entity reconciliation pipeline that resolves translation ambiguities and address discrepancies.
2. Pipeline Design and Execution Flow
Extraction Phase: The agent extracts any occurrence of manufacturer corporate names, factory names, and manufacturing plant addresses across all submitted documents.
Standardization Engine:
Address text is normalized through a rule-based parser that handles common contractions (e.g., converting STE, UNIT, FL to Suite, Unit, Floor).
English street names and entities are cross-referenced with local Taiwanese address conventions to generate corresponding Chinese translations.
Fuzzy Semantic Matcher:
The agent calculates Levenshtein distances and semantic cosine embeddings for corporate entity records, checking them against registered databases to identify variations (e.g., classifying "Acme Diagnostics Corp" and "Acme Biotech Inc." as potential corporate branch office alignments).
Resolution Prompt Workflow:
When an address variation is identified, a specialized agent prompt resolves the mismatch:
code
Code
[System Input]: Address_A: "STE 400, 100 Innovation Way, Boston, MA 02111", Address_B: "Unit 400, 100 Innovation Way, Boston, MA 02110"
[Task]: Validate the geographical consistency of these addresses.
[Reasoning Path]: 
  1. Are the street coordinates identical? (Yes, '100 Innovation Way').
  2. Are 'STE 400' and 'Unit 400' synonymous in US real estate registries? (Yes, office suite abbreviations).
  3. Identify the ZIP code variance detail (02110 is Boston central, 02111 is the adjacent Innovation district).
[Output JSON Schema]:
  {
    "resolved": true,
    "equivalence_score": 0.95,
    "error_type": "Minor spelling and postal sector mismatch",
    "explanation_zh": "原廠授權書與CFSM之郵區編號 02110 與 02111 實屬同街區鄰近劃分，且 STE 400 與 Suite 400 軟性定位完全一致...",
    "suggested_mitigation_statement_en": "The manufacturer confirms that 'Suite 400', 'STE 400', and 'Unit 400' refer to the identical physical manufacturing facility..."
  }
Exporter Interface:
Generates a bilingual Address Alignment Statement (地址一致性勘誤核對函) that can be appended directly to the official response letter, allowing the auditor to bypass a full CFSM amendment process.
5.2 WOW AI Feature B: Automated CyberSecurity SBOM & SaMD Threat Modeling Agent (資安網安威脅建模代理)
1. Description and Regulatory Pain Point
Under my-made TFDA and FDA medical guidelines (such as Taiwan's 醫療器材網路安全查驗登記審查要點), any Software as a Medical Device (SaMD) or hardware system containing network capabilities (WiFi, Bluetooth, telemetry) must submit a Software Bill of Materials (SBOM) alongside a Cybersecurity Threat Modeling Report. Manufacturers frequently fail to submit these reports, omit core software dependencies, or fail to account for system vulnerabilities.
This feature parses technical software specifications and simulated network logs to reconstruct an interactive SBOM and generate a regulatory-grade Cybersecurity Threat Diagram and Vulnerability report aligned with TFDA guidelines.
code
Code
[ Technical Specs / Configuration Input ] 
                           |
                           v
          [ Dependency & Protocol Extraction ]
                           |
                           v
        [ SBOM Reconstruction & CVE database lookup ]
                           |
                           v
           [ Attack Tree Simulation (STRIDE) ]
                           |
                           v
        [ TFDA Cybersecurity Compliance Checklist Mapping ]
2. Pipeline Design and Execution Flow
SBOM Parsing: The agent scans software specifications, repository manifests (e.g., package.json), and build configurations to extract open-source dependencies, firmware libraries, and communication protocols (e.g., Bluetooth Low Energy 5.0, HTTPS/TLS 1.3).
CVE database lookup:
Cross-references identified dependencies against known security vulnerability catalogs (NVD/CVE databases) to flag out-of-date or vulnerable packages.
STRIDE Attack Tree Simulation:
Constructs a threat vectors diagram using the STRIDE framework (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege):
Spoofing Threat: Intercepting on-device bluetooth telemetry.
Information Disclosure: Unprotected transmission of PPG or ECG raw signals over local HTTP networks.
Implementation Blueprint (Backend Router Example):
code
Ts
app.post("/api/audit/cybersecurity", async (req, res) => {
  const { software_spec } = req.body;
  const response = await ai.models.generateContent({
    model: "gemini-2.5-flash",
    contents: `Review this SaMD firmware specification: "${software_spec}". Reconstruct its SBOM, identify security risks based on STRIDE, and check alignment with TFDA Cybersecurity guidelines. Return JSON.`,
    config: { responseMimeType: "application/json", responseSchema: cyberSecuritySchema }
  });
  res.json(response.text);
});
User Interface Output:
Renders an interactive Cybersecurity Threat Dashboard inside Panel 2. This displays a visual nested tree of CVE vulnerabilities, flags software packages that violate regulatory guidelines, and provides recommended patches (e.g., "Enforce TLS 1.3 encryption on port 443 with SHA-256 cipher suites").
5.3 WOW AI Feature C: Multi-Institutional Clinical Test Cohort Data-Contamination & Demographic Overlap Detector (臨床驗證數據多中心重疊與去偏誤偵測器)
1. Description and Regulatory Pain Point
During clinical validation audits for medical device software, clinical research organizations (CROs) must demonstrate that their testing datasets are mathematically isolated from their machine learning training datasets. If patient records leak between these cohorts (known as Data Contamination or Data Leakage), validation performance metrics like Accuracy, Sensitivity, and ROC AUC will be artificially inflated, masking overfitting and posing patient safety risks.
This feature deep-scans technical clinical validation text reports, extracting statistical profiles (mean values, patient age, gender distributions, clinical histories) and cross-referencing patient cohort matrices. It alerts auditors to mathematical sample leaks, and provides recommendations for rebuilding unbiased testing cohorts.
2. Pipeline Design and Execution Flow
Statistical Profiling Engine:
The agent extracts key metadata from both the training and testing cohort descriptions, including sample sizes, mean age, standard deviations, gender distributions, and clinical diagnostic classifications.
Mathematical Overlap Audit:
The engine parses the numeric distributions and cohort identifiers. For example, if Chapter 8 lists a training cohort drawn from "Boston-A6 (Patient IDs 10001 to 10250)" and the validation set features "Boston-A6 Validation Subset (Patient IDs 10232 to 10249)", the agent calculates the overlapping set intersection:
Data Contamination Severity Matrix:
Critical (
 Leak): Training and validation sets are heavily mixed. Results in a mandatory fail recommendation.
Medium (
 Leak): Minor leakage detected. Requires the submission of an independent testing dataset.
None: Complete mathematical isolation of validation cohorts.
Prescriptive Fix Recommendation Workflow:
The agent calculates estimated impact metrics (e.g., predicting that removing contaminated patient subsets will cause an estimated drop in verification AUC from 
 to 
). It then drafts a custom remediation plan:
code
Code
[REMEDIATION PLAN]
1. EXCLUDE: Instantly omit the 18 overlapping patients (IDs 10232 to 10249) from the validation dataset.
2. EXPAND: Source 50 clean clinical registers from an independent clinical center (e.g., New York clinical group, IDs 10501 to 10582).
3. VERIFY: Recompute the ROC curve and declare the updated independent performance index.
User Interface Output:
Visualized as Graph 5 (Venn Diagram), displaying the exact mathematical overlapping region. Clicking the overlap displays the compromised patient IDs, providing auditors with clear, actionable evidence for their deficiency letters.
6. BACKEND ENGINEERING & SERVER-SIDE PROMPT GUIDELINES
The platform is designed as an Express and Vite full-stack application. To ensure security, secret credentials (such as process.env.GEMINI_API_KEY) are stored and used exclusively on the server side, keeping them insulated from the client's browser.
code
Code
+------------------------------------------------------------------------------------------------------------------+
|                                              SERVER-SIDE ARCHITECTURE                                            |
|                                                                                                                  |
|  [ Client Browser Requests ] ---> Express Server Engine (server.ts, Cwd Workspace Root)                           |
|                                         |                                                                        |
|                                         +---> Router: POST /api/review                                           |
|                                         |       |                                                                |
|                                         |       +---> Ingests Materials, Active Skill                            |
|                                         |       +---> Calls @google/genai SDK (GEMINI_API_KEY)                    |
|                                         |       +---> Enforces strict JSON Schema constraints                    |
|                                         |                                                                        |
|                                         +---> Router: POST /api/chat                                             |
|                                                 |                                                                |
|                                                 +---> Ingests Conversational queries & Current state             |
|                                                 +---> Generates dynamic regulatory advice                        |
+------------------------------------------------------------------------------------------------------------------+
6.1 Server Route 1: Post Dossier Review (/api/review)
This endpoint handles the core analytical workload. It accepts the unstructured dossier text (materials), the customized skill instructions (skill), and the requested model name, returning a structured JSON response matching the AnalysisResult schema.
API Signature & Headers:
Method: POST
Endpoint: /api/review
Headers: Content-Type: application/json
Request Body Schema:
code
JSON
{
  "materials": "string",
  "skill": "string",
  "model": "string"
}
System Prompt Blueprint and Chain-of-Thought Guardrails:
To guarantee reliable and consistent analysis, the AI model is instructed with a comprehensive system prompt:
code
Code
You are an elite TFDA and FDA pre-market notifications reviewer.
You are examining a dossier submission against a set of statutory chapters and skills.
Perform your review in five sequential steps:
1. Profile Extraction: Locate and normalize all corporate name references, addresses, and model versions.
2. Discrepancy Reconciliation: Cross-tabulate manufacturer factory address elements. Flag inconsistencies such as "Suite" vs. "Unit".
3. Continuous Learning Drift Audit: Scan for adaptive ML parameters. If discovered, flag the absence of a post-market algorithm protocol.
4. Clinical Contamination Audit: Compare training and testing patient cohorts. Identify overlapping records and calculate contamination percentages.
5. Checklist Mapping: Map findings to the provided statutory checklist, recommending Pass, Fail, or N/A status for each item.

You MUST return your output strictly in JSON, conforming to the requested schema. Do not include markdown code ticks outside of the json block.
6.2 Server Route 2: Copilot Consult Chat (/api/chat)
This endpoint powers the virtual regulatory advisory chatbot in Panel 3. It maintains context by ingesting the conversation history, the active dossier materials, and the current state of checklist overrides to provide highly relevant, context-aware responses.
API Signature & Headers:
Method: POST
Endpoint: /api/chat
Headers: Content-Type: application/json
Request Body Schema:
code
JSON
{
  "message": "string",
  "history": [
    { "role": "user" | "model", "text": "string" }
  ],
  "materials": "string",
  "current_findings": "object"
}
Prompt Engineering Strategy:
The server system injects the full materials context and the current current_findings schema directly into the conversation history:
code
Code
You are a Regulatory Expert Co-Pilot counseling a human TFDA auditor.
You are reviewing the active workspace data:
=== DOSSIER MATERIALS ===
{materials}
=== ACTIVE WORKBOOK OVERRIDES ===
{current_findings}

Generate responses that are practical, objective, and reference my-made TFDA statutes (e.g., 醫療器材管理法, 510(k)). 
When explaining deficiencies, provide clear examples of response letter drafts (補件回覆函草稿碼說明) that manufacturers can use to address the gaps.
6.3 Lazy-Loaded SDK Initialization & Production Build Pipelines
As highlighted in the system integration guidelines, SDK clients that require external API keys must be initialized lazily at runtime to prevent application crashes during the build phase if keys are missing.
code
TypeScript
// server.ts - Lazy Key Loading Mechanism
import { GoogleGenAI } from "@google/genai";

let aiInstance: GoogleGenAI | null = null;

export function getAIClient(): GoogleGenAI {
  if (!aiInstance) {
    const key = process.env.GEMINI_API_KEY;
    if (!key) {
      console.warn("⚠️ [Initialization Warning] GEMINI_API_KEY environment variable is missing.");
      throw new Error("GEMINI_API_KEY is required to execute AI Regulatory audits.");
    }
    aiInstance = new GoogleGenAI({ apiKey: key });
  }
  return aiInstance;
}
To ensure smooth compilation and deployment in Node.js environments, the root package.json build and execution scripts are configured with TypeScript bundle compilation via esbuild:
code
JSON
{
  "scripts": {
    "dev": "tsx server.ts",
    "build": "vite build && esbuild server.ts --bundle --platform=node --format=cjs --packages=external --sourcemap --outfile=dist/server.cjs",
    "start": "node dist/server.cjs"
  }
}
This guarantees that:
npm run dev monitors TypeScript changes in real-time.
npm run build compiles client-side assets to /dist and bundles the Express server.ts entry point into a single CommonJS file (/dist/server.cjs). This prevents module-path compilation issues and boosts startup speed.
7. 20 COMPREHENSIVE REGULATORY FOLLOW-UP QUESTIONS (諮詢法規探針)
These twenty highly detailed regulatory follow-up questions are embedded into the bottom panel of the workspace. Clicking any of these questions sends them directly to the Copilot Consult Chat Engine to assist human auditors in evaluating complex applications.
Category I: Administrative Auditing & Entity Verification (行政與資格審結)
品名一致性衝突 (Brand Consistency Analysis):
Question: "本產品英文品名為 SmartHeart Monitor Pro，然而原廠國外授權書 (LoA) 載明之品名卻為 SmartHeart Diagnostics System (包含配件 M1、M2、M3)，此類品名不合致 (Discrepancy) 是否會直接導致 TFDA 做出退件或限期補正宣告？應如何撰寫官方澄清函以求一次性通關？"
廠址縮寫文字偏誤 (Address Abbreviation Alignment):
Question: "在製售證明 (CFSM) 上的製造廠地址登記為 'Suite 400, 100 Innovation Way, Boston'，而在品質管理系統 (QMS/QSD) 認可登錄函上卻為 'STE 400, 100 Innovation Way, Boston'。此類 administrative variation 在 TFDA 的實務審查中是否需主動開立缺失？有無簡便的地址一致性對齊切結書 (Address Alignment Statement) 標準模板與免除重辦 CFSM 手續之通融條款？"
授權書郵區編號登載錯誤 (Zip Code clerical error in LoA):
Question: "國外製造商原廠授權書 (LoA) 中不慎將製造廠廠址郵遞區號錯寫為 02110 (實際應為 02111)，但其他路名、廠家名稱皆為正確。這套查驗登記申報若被審查員揪出，是否可在不更動英文 LoA 原本、不要求原廠重新簽署宣誓書的情況下，藉由原廠出具對照說明公文 (Clerical Error Explanation) 來完成手續？"
子母公司委託合約豁免 (Affiliated Entity Contract Waiver):
Question: "若申請查驗登記之藥商 (Applicant Entity) 與國外製造商 (Manufacturer Entity) 屬同一跨國醫療集團之子母公司關係，其雙方之製售授權公務往來是否仍強制檢附獨立的「委託製造契約書」？在申報 TFDA 第二等級軟體醫療器材 (SaMD) 時，是否有簡化委託關係證書之相關行政例外規定？"
製售證明過期基準與型號對比 (CFSM Expiration Constraints):
Question: "當原廠檢附之美國 FDA 自由銷售證明 (CFSM) 發文日期已瀕臨兩年效期，但其登載之 Class II 產品型號與我國中文仿單申請草案完全一致時，審查員在查驗實務上會直接予以拒絕核登，抑或是會要求藥商切結「保證原廠於查驗審查期間仍持續生產且具備 Freely Marketable 狀態」之承諾書？"
Category II: Quality Management Systems & Site Registration (品質管理系統核配 QMS/QSD)
軟體醫材免除部分製程規格 (SaMD Labeling/Packaging Exemption):
Question: "對於無實體硬體、完全以軟體交付 (Software as a Medical Device - SaMD) 之第二等級醫療器材委託製造廠，其 QMS (QSD) 認可登錄範圍中若不包含任何「包裝」、「滅菌」及「貼標」等傳統物理製程，是否可合理豁免提交「標籤與包裝製程說明文件」？在 TFDA 審查時應如何撰寫此類豁免說明？"
委託製造貼標名稱規範 (Contract Manufacturing Labeling Specs):
Question: "若本品之原廠製造委託了第三方專業代工廠 (OEM) 生產，但在申請書上標註之製造廠為 Acme Biotech Inc.，則產品包裝及中文仿單上對於 'Manufactured by' 與 'Manufactured for' 的廠家名稱、地址登載，應如何與 QSD 認可登錄函保持合致，方能符合我國《醫療器材管理法》之中文標籤規範？"
QMS 認可登錄品項代表性比照 (QMS System Product Line Matching):
Question: "現有 QMS (QSD) 許可函所核准登錄之產品分類品項代碼 (例如：E.3620 智慧型心電圖生理分析軟體)，如何證明能完全覆蓋並代表本次申請查驗之「CardioNet-v4 classifier 動態 arrhythmial 分析軟體」之技術結構與製程？"
QMS 效期與展延證明查驗 (QMS Expiration & Extension Evaluation):
Question: "若本案所檢附之 QMS 認可登錄證書將於 18 個月內過期，TFDA 查驗登記審查員是否會依循慣例，要求申請藥商主動檢附「已向衛福部提出展延申請之收件憑證及承諾書」，始得繼續進行 510(k) 技術審查？此處之時效風險應如何評估控制？"
無滅菌製程 SaMD 之 QSD 簡化流程 (Simplified QSD and ISO 13485 Standards):
Question: "當國外製造廠已持有最新 ISO 13485:2016 證書，且其製造項目為純軟體 SaMD。在申請我國 QSD 認可登錄時，可否採用簡化模式 (Simplified QSD) 進行書面審查？應提送哪些代表性品質手冊章節以證明其軟體生命週期管理（符合 IEC 62304 / ISO 62304）之健全性？"
Category III: Labeling, IFU & Regulatory Claims (標籤仿單與宣稱基準)
中文仿單次級療效越界缺失 (IFU Off-Label Claim Penalties):
Question: "若中文仿單（擬稿）中依據國外原廠型錄翻譯，宣稱其搭載之 CNN 演算法可偵測高達 15 種心律不整狀態，然而原廠臨床驗證報告僅就心房顫動 (Afib) 與心室頻脈 (VT) 二種核心指標提供完整統計學 Sensitivity 與 Specificity，審查員會如何判定？是否會直接對該療效涉虛偽誇大開立缺失，並限縮其僅能宣稱 Afib 與 VT 偵測？"
警語免除與法定備註 (Exemption of Label Warnings):
Question: "中文標籤草擬稿若未標示「本產品不核定用作急診心臟監測之主要判定依據」，是否屬於我國《醫療器材管理法》中規避限縮警語之缺失？審查員一般會引用何種查驗指引（如衛福部近年發布之醫用軟體標籤警語規範）強制要求加註？"
軟體版本與仿單版本一致性 (SaMD Version Configuration Control):
Question: "中文仿單草案及規格表上所登載之軟體版本為 v4.2.1-Alpha，但臨床報告及技術文件中使用的開發版次為 v4.0.0。這類版次不一致是否會構成重大技術補正要件？在軟體生命週期組態管理 (Configuration Management) 中，版本退回、次級修改應如何說明，方能消除開發版本與核定版本之技術落差疑慮？"
選配件圖片與核定規格表對比 (Optional Accessories & Photo Proof Consistency):
Question: "原廠說明書中列配之部分選配傳感器配件（例如 M1、M2），若未包含在台灣本次申請之查驗主型號規格內。中文仿單草案是否應主動塗銷或遮蔽該選配件之彩色實貼圖片？如何避免因選配件型號未申報，而導致整份說明書被認定「非本次查驗產品範圍」之行政延誤？"
委託製造受託廠資訊法定揭露 (Contractor vs Manufacturer Address specifications):
Question: "涉及全部製程委託製造之產品，其貼標與說明書上的受託代工廠名稱及廠址資訊（如位於波士頓之代工廠），是否必須在中文仿單及查驗登記申請書中「製造廠」與「藥商」欄位同時登載並揭露？若揭露格式不一致（例如縮寫、大小寫及郵區差異）會對案件審結造成何種影響？"
Category IV: Algorithms, CyberSecurity & Clinical Contamination (演算法確效、資安與臨床污染審查)
演算法動態學習核登禁忌 (Adaptive SaMD Post-Market Protocol Gaps):
Question: "本品搭載之 CardioNet-v4 演算法具有動態 backpropagation 持續學習機制 (Adaptive Neural Network)。依據 TFDA 最新之《人工智慧醫療器材查驗登記審查指引》，為何此類「非鎖定狀態 (Non-Locked State) 演算法」不允許直接以一般 510(k) 軟體變更程序核准？製造商必須檢附何種持續學習監控計畫與模型漂移防範機制 (Model Drift Mitigations)？"
臨床驗證數據污染實務判例 (Data Contamination Impact on Diagnostics Clinical Trial):
Question: "當審查員發現本案的驗證集與訓練集出現 18 筆病患 identifiers 交叉重疊（重複使用 Massachusetts 相同機構統計點），這在統計學上構成什麼資料污染 (Data Contamination/Leakage) 效應？這對所宣稱之 Sensitivity 99.1% 之科學信度 (Scientific Credibility) 將帶來何種負面影響？退件重做之判定原則為何？"
資安規範資料傳輸安全性確效 (TFDA Cybersecurity and GDPR Data Encryption Rules):
Question: "對於經由藍牙與手機 App 同步之穿戴式醫療監測軟體，申請查驗登記時若未提供「防止未受權介入與資料外洩之防護機制」與滿足 TLS 1.3 傳輸加密確效。補正時是否可以原廠 Declaration Letter（宣告信）代替？抑或必須提交完整之弱點掃描 (Vulnerability Scan)、滲透測試 (Penetration Test) 與威脅建模 (Threat Modeling STRIDE) 數據報告？"
電磁相容與安全標準版本退役缺失 (IEC 60601-1-2 EMC Standard Update Compliance):
Question: "本品所檢附之電氣安全 (IEC 60601-1) 與電磁相容 (IEC 60601-1-2) 測試報告係於 2022 年完成，若其報告版本與我國目前已強制執行之最新版調和標準（調和至最新四版加強型）有所落差，審查員是否會要求重新至 TFDA 認可之國內醫療器材測試實驗室補測？如何主張原創等同性確效 (Equivalence Claim) 以求免予重測？"
清潔確效與化學殘留量可接受極限 (Reprocessing & Disinfection validation for sensors):
Question: "對於與人體表面皮膚接觸之動態穿戴式心律感測器，審查員要求補正「清潔與重複消毒確效測試報告」(Reprocessing validation)。廠商應如何選擇適當之化學消毒劑及其濃度（例如使用 70% 異丙醇）以證明清潔確效？其刺激性與致敏性測試 (Cytotoxicity, Sensitization) 數據應如何與生物相容性 ISO 10993 系列標準對齊以求符合臨床安全性？"
8. SUMMARY OF COMPLIANCE
By integrating the "Professional Polish" Design Theme, this technical specification establishes a distinctive, authoritative layout that prioritizes cognitive clarity and information density. The layout arranges complex documentation, nested checklist workbooks, micro-animated SVG compliance graphs, and an interactive NLP consulting agent into a clean three-panel workspace. The platform provides regulatory auditors with an efficient, data-driven sandbox to review complex dossier submissions, identify administrative discrepancies, verify algorithm health, and ensure patient safety.
