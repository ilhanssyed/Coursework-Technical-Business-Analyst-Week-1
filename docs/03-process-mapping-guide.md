# Phase 3: Process Mapping & Diagnosis

## Task 2: Pain-Point Overlay (Grounded System Failures)

To turn this process map into a diagnostic tool, five critical operational failure points have been overlaid directly onto the workflow sequence. Each bottleneck is explicitly verified by raw activity logs or stakeholder testimony:

### [PP-01] Administrative Waste Loop (Overlaid on Phase B - Step H)
* **Process Location:** The Shift-Prep & System Switching phase.
* **The Break:** Agents are forced to execute manual, cross-system status verification checks (`spreadsheet_reconcile`) because there is no unified view of account states upon logging in.
* **Data & Evidence Trace:** `recovery_activity_tracker.csv` logs routine instances (e.g., `ACT-07318`, `ACT-09300`) where agents spend **8 to 12 minutes per file** cross-referencing the legacy database, local trackers, and emails, frequently resulting in an operational outcome of `next_action_unclear`.

### [PP-02] Redundant Verification Layer (Overlaid on Phase C - Step J)
* **Process Location:** Pre-Outreach Sequence.
* **The Break:** Because data updates are siloed and slow, agents have zero confidence in the accuracy of their static desktop spreadsheets. They execute repeated, duplicate status checks before dialing a phone number to make sure a colleague didn't touch the account overnight.
* **Data & Evidence Trace:** `recovery_activity_tracker.csv` explicitly flags these repeated checks with **`duplicate_check_flag = Y`** (e.g., `ACT-00003`), confirming a massive drain on active shift capacity.

### [PP-03] Core Tracking Discrepancy & System Blindness (Overlaid on Phase D - Step T)
* **Process Location:** Data Capture / Promise Registration.
* **The Break:** The 20-year-old core system architecture contains an architectural defect—it cannot programmatically differentiate between a customer's verbal commitment to pay and an actual cash confirmation clearing the ledger. This forces a dual-logging vulnerability where agents must type text notes into the DB and copy them to Excel.
* **Data & Evidence Trace:** `stakeholder_interview_notes.csv` (ID: **`SN-126`**) — *"The current system treats payment promises the same as payment confirmations, which creates confusion."*

### [PP-04] Operational Limbo & Deadline Enforcement Failure (Overlaid on Phase E - Step Z)
* **Process Location:** Post-Outreach Tracking / Payment Due Date.
* **The Break:** When a customer misses a promise-to-pay deadline, the database remains completely silent. It fails to enforce dates, trigger flags, or surface the file back to the agent. Files sit abandoned in intermediate statuses until an agent manually audits their desktop sheet.
* **Data & Evidence Trace:** `stakeholder_interview_notes.csv` (ID: **`SN-118`**) — *"Cases get stuck in 'pending callback' status indefinitely because the callback date is never enforced."* This blindspot drives our operational **14% missed follow-up rate (FA-06)**.

### [PP-05] Random Outreach Sequencing (Overlaid on Phase A - Step C)
* **Process Location:** Ingestion Queue & Dialing Execution.
* **The Break:** Because the 100,000+ portfolio sits in a flat, unsegmented queue, agents reach out to customers in a random order. High-priority, high-propensity accounts are starved of attention while low-complexity, routine balance inquiries clog up live phone lines.
* **Data & Evidence Trace:** `stakeholder_interview_notes.csv` (ID: **`SN-119`**) — *"We reach out to customers in a random order rather than any strategic sequence."*




---

## Task 3: Strategy, Eligibility Matrix & Opportunity List

To resolve the operational capacity gaps identified in our As-Is process, we must cleanly decouple routine, transactional touchpoints from complex collections portfolios. 

### 1. The Core Eligibility Filtering Rule
Following a strict data triage methodology, our system design filters incoming volume using two structural tracks based on the **38% Straightforward Case Share (FA-03)** baseline:

* **Automated Self-Service Path Eligibility:** Accounts must fall into the `low` or `mid` risk bands, have zero open contractual balance disputes, and exhibit repeatable, highly transactional behavior (such as simple balance queries or routine updates).
* **Mandatory Agent-Led Path Reservation:** Accounts are permanently blocked from self-service automation loops if they match any criteria outlined in the matrix below. These files skip portal interaction completely and drop straight into an agent's daily prioritized batch queue.

### 2. Operational Pathway Matrix

| Triage Parameter | Operational Pathway | Core System Logic & Justification | Data & Evidence Source |
| :--- | :--- | :--- | :--- |
| **Active Balance Dispute** | 🔴 **Strict Agent-Led** | Requires complex verification, investigative cross-referencing, and specialized legal compliance judgment. | `stakeholder_interview_notes.csv` (ID: **`SN-120`**) |
| **Severe Customer Hardship / Vulnerability** | 🔴 **Strict Agent-Led** | Demands deep human empathy, non-standard options, and subjective regulatory forbearance evaluation. | `stakeholder_interview_notes.csv` (ID: **`SN-121`**) |
| **High-Risk Credit Bands** | 🔴 **Strict Agent-Led** | Flagged exceptions where backend validation marks account risk parameters as volatile or highly unpredictable. | `smart_recovery_portal_events.csv` (`risk_band = high` $\rightarrow$ `ineligible`) |
| **Routine Balance Check** | 🟢 **Self-Service Portal** | Highly repeatable, high volume, low risk. Completely suitable for direct unassisted digital execution. | `finance_assumptions.csv` (ID: **`FA-03`** / 38% case share) |
| **Repayment Term Selection** | 🟢 **Self-Service Portal** | Menu-driven, rules-governed transaction paths utilizing standardized, pre-approved financial parameters. | `finance_assumptions.csv` (IDs: **`FA-07`**, **`FA-08`** uplifts) |

### 3. First-Pass Automation Candidate Shortlist
The following list identifies five strategic capabilities intended for development. These items are structured to address the specific friction points mapped in our process, laying out the explicit foundation for our Phase 4 financial ROI model.

#### OP-01: Self-Serve Account Summary
* **Capability Description:** Provides a secure digital interface for low/mid-risk delinquent customers to view their live outstanding balance and historical statement breakdowns privately.
* **Target Business Process Area:** Internal Agent Morning Prep & Account Status Verification Loops.
* **Friction Points Addressed:** Directly eliminates the administrative bottleneck where live phone queues are clogged with routine account lookups, cutting out manual `status_check` loops.
* **Pre-vetted Implementation Cost Baseline:** **£45,000** (Low Complexity Asset — `FA-10`)

#### OP-02: Digital Promise-to-Pay Capture
* **Capability Description:** Enables authenticated portal users to select and lock in a specific, legally compliant repayment deadline directly within the web interface.
* **Target Business Process Area:** Data Capture, Notes Writing, & Post-Outreach Promise Registration.
* **Friction Points Addressed:** Bypasses the system defect where verbal commitments are logged as free text. The portal writes the promise date programmatically as a hard validation rule, addressing the **14% missed follow-up rate (FA-06)**.
* **Pre-vetted Implementation Cost Baseline:** **£85,000** (Medium Complexity Asset — `FA-11`)

#### OP-03: Eligible Payment-Plan Selection
* **Capability Description:** An interactive, rules-driven repayment layout that allows eligible customers to self-enroll in structured monthly repayment schedules.
* **Target Business Process Area:** Manual Negotiation, File Assessment, & Account Setup.
* **Friction Points Addressed:** Diverts a massive portion of the **38% straightforward case volume (FA-03)** away from the manual telephony queue, ensuring that live agent hours are preserved for complex customer files.
* **Pre-vetted Implementation Cost Baseline:** **£85,000** (Medium Complexity Asset — `FA-11`)

#### OP-04: Contact Detail Update Request
* **Capability Description:** A self-service interface allowing customers to submit changes to profiles, addresses, or telephone contact options directly.
* **Target Business Process Area:** Contact Maintenance & System Syncing.
* **Friction Points Addressed:** Prevents a single customer from accumulating duplicate records (`SN-010`) across varying points of entry by centralizing detail capture.
* **Pre-vetted Implementation Cost Baseline:** **£45,000** (Low Complexity Asset — `FA-10`)

#### OP-05: Rules-Based Backend Routing Engine
* **Capability Description:** An automated backend routing system that evaluates DPD thresholds, risk bands, and active dispute flags to distribute prioritized, daily batched agent queues.
* **Target Business Process Area:** Morning Allocation & Queue Prioritization.
* **Friction Points Addressed:** Resolves the problem where agents work files in a random sequence (`SN-119`) by delivering prioritized daily queues.
* **Pre-vetted Implementation Cost Baseline:** **£85,000** (Medium Complexity Asset — `FA-11`)


## Task 1: As-Is Process Map

Below is the dynamic current-state process flow representing the actual, unvarnished day-to-day workflow lived by the collections team. It maps an account from initial delinquency entry to final manual outcomes and silent tracking loops.

```mermaid
flowchart TD
    %% Styling Configuration
    classDef actor fill:#f9f,stroke:#333,stroke-width:2px;
    classDef system fill:#bbf,stroke:#333,stroke-width:2px;
    classDef break fill:#ff9,stroke:#f00,stroke-width:2px;
    classDef handoff fill:#bfb,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5;

    %% Ingestion Section
    subgraph Phase_A [Phase A: Queue Ingestion & Inflow]
        A[Contractual Due Date Breached] --> B[(20-Year-Old Legacy DB)]
        B --> C{100k+ Account Queue}
        C -->|Unsegmented Mix| C1[Routine Inquiries]
        C -->|Unsegmented Mix| C2[Complex Financial Disputes]
    end

    %% Agent Morning Waste Loop
    subgraph Phase_B [Phase B: The Agent Shift-Prep Waste Loop]
        D[Agent Logs In] --> E[Open Legacy DB to Fetch IDs]
        E --> F[Open Local Desktop Excel Spreadsheet]
        F --> G[Open Outlook Email Inbox]
        G --> H[Execute manual 'spreadsheet_reconcile']
        H -->|8-12 Mins Spent| I{Outcome Code Check}
        I -->|Outcome: Next Action Unclear| G
        I -->|Outcome: Context Reconciled| J[Pre-Outreach Status Check]
    end
    
    %% Duplication & Telephony
    subgraph Phase_C [Phase C: Outreach & Telephony Interaction]
        J -->|duplicate_check_flag = Y| K[Manual Dial via Phone]
        K -->|AHT: 18 Minutes| L{Is Customer Reachable?}
        L -->|NO| M[Leave Voicemail / Trigger SMS Link]
        M -->|Manually Type Call Note in Legacy DB| N[Update Personal Excel Tracker]
        N -->|Loop to Next Account File| E
        
        L -->|YES| O[Execute Live Phone Negotiation]
    end

    %% Capture Gaps & Hand-offs
    subgraph Phase_D [Phase D: Negotiation & Data Capture Failure]
        O --> P{Negotiation Outcome?}
        P -->|Customer Disputes Balance| Q[Flag Account Row]
        Q -->|HAND-OFF| R[\Specialist Dispute Review Team/]:::handoff
        
        P -->|Promise-to-Pay PTP Made| S[Record Verbal Promise Terms]
        S -->|System Limitation: SN-126| T{Legacy Architecture Rule}
        T -->|Treats Promise same as Cash Confirmation| U[Type Text Deadlines into Legacy DB Notes Field]
        U -->|Manual Duplication Error| V[Manually Key Terms into Desktop Spreadsheet Tracker]
    end

    %% Post Outreach Limbo Loop
    subgraph Phase_E [Phase E: Post-Outreach Tracking Limbo]
        V --> W{Payment Kept on Due Date?}
        W -->|YES| X[Cash Clears Bank Ledger via Overnight Batch]
        X --> Y([File Advanced toward Closed Status])
        
        W -->|NO: Payment Fails Silently| Z[System Remains Completely Silent]
        Z --> AA[Account Sits in Operational Limbo]
        AA -->|Relies 100% on Human Memory| AB{Does Agent Inconsistently Audit Tracker?}
        AB -->|YES: Caught Weekly| E
        AB -->|NO: Missed Follow-Up Rate: 14%| AC[Account Leaks Value Silently]
        AC -->|Ages into High Risk Band| AD[HAND-OFF]
        AD --> AE[\Amina's Monthly Portfolio Performance Review/]:::handoff
    end

    %% Node Customizations
    H:::break
    J:::break
    U:::break
    V:::break
    Z:::break



    