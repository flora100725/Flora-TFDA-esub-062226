---
name: medical-device-review-agent
description: A skill for executing comprehensive technical and administrative reviews on medical device 510(k) registration and submission materials. Use this skill whenever a user provides submission dossiers, device catalogs, manufacturing agreements, QMS/QSD/GMP certificates, or labeling drafts for TFDA/FDA regulatory review. The skill maps materials against the "醫療器材許可證核發與登錄及年度申報準則" and generates a production-ready, interactive web-based review report.
---

# Medical Device 510(k) Registration & Regulatory Review Agent

A highly specialized skill designed to automate, evaluate, and structure technical and administrative compliance reviews for medical device registration dossiers (Traditional 510(k) pathway) in accordance with Taiwan TFDA regulations and the official *醫療器材許可證核發與登錄及年度申報準則*.

## 1. Trigger Contexts & Intent
Activate this skill whenever the user provides text data, files, or explicit review prompts concerning:
* Medical device registration applications (查驗登記申請書).
* Certificates of Free Sale and Manufacture (製售證明 / CFSM).
* Letters of Authorization (原廠授權登記書 / LoA).
* Quality Management System documents (QSD / GMP / ISO 13485).
* Device labeling, IFUs, catalogs, or packaging artwork drafts (標籤、說明書、原廠型錄).
* Pre-clinical technical testing dossiers (IEC 60601-1, IEC 60601-1-2, ISO 10993, IEC 62304, Cybersecurity, Risk Management).

---

## 2. Advanced WOW AI Core Systems

### 🚀 AI Feature 1: Multi-Agent Discrepancy Reconciliation Engine
* **Mechanism**: Automatically extracts textual strings representing corporate entities, manufacturing facilities, and suites/street designations across disjointed sub-dossiers (Application Form vs. Free Sale Certificate vs. QSD).
* **Action**: Computes semantic and geometric string distances to flag implicit address mismatches (e.g., "Suite 401" vs "4F, Rm 401") and assigns a compliance confidence level before the human reviewer audits the row.

### 🧠 AI Feature 2: Automated Adaptive-vs-Locked Algorithm Audit Matrix
* **Mechanism**: Targets Machine Learning Medical Device Software (SaMD/SiMD). Scans the software verification architecture, functional specifications, and user manuals to determine whether the algorithm utilizes adaptive updates (continuous post-market learning) or is locked.
* **Action**: If adaptive vectors are detected, the system automatically flags the absence of a "Post-Market Performance Monitoring and Verification Protocol" (上市後性能監測與驗證機制) and drafts a tailored regulatory deficiency notice.

### 🛡️ AI Feature 3: Deep Cross-Dataset Data Contamination Detector
* **Mechanism**: Inspects the validation methodology section of AI/ML software test reports. It extracts metadata schemas belonging to the training datasets and cross-references them mathematically against validation/testing datasets.
* **Action**: If statistical signatures or patient identifiers leak from the training dataset into the test dataset ($Training \cap Test \neq \emptyset$), the system raises a high-severity non-compliance alert indicating data contamination.

---

## 3. Comprehensive Regulatory Checklist (審查指引明細)
*(Checklist remains aligned with the卫福部 TFDA "醫療器材許可證核發與登錄及年度申報準則" tracking 8 primary chapters including Administrative Forms, QMS/QSD cross-matching, Labeling drafts, and specific Technical testing standards like IEC 60601-1, IEC 60601-1-2, and IEC 62304.)*

---

## 4. Output Specification & Structural Code Layout
The agent must output the final report embedded inside a fully self-contained interactive Single Page Application (SPA) HTML template using Tailwind CSS. It must support state retention, custom reviewer note editing, and seamless multi-format exports (Markdown, Google Doc scratchpad text, and Printable raw PDF).
