# JTBD and Prioritisation

## Step 1: Group the evidence

We've grouped the qualitative data from stakeholder interviews into six core themes showing exactly where the system is breaking down:
* **Duplicate work:** Multi-file tracking sheets and manual cross-referencing drain agent time.
* **Missed follow-up:** Inconsistent outreach timing across the 100,000 delinquent account pool.
* **Poor visibility:** Lack of real-time account context during channel hand-offs.
* **Customer friction:** Repetitive contact journeys and long phone hold times for simple balance checks.
* **Financial credibility:** The baseline mandate to isolate hard operational cost-out from soft uplifts.
* **Change resistance:** Operational distrust of real-time noise and unvetted automation features.

---

## Step 2: Build an evidence table

| Stakeholder | Quote or observation | Theme | Business impact | Confidence |
| :--- | :--- | :--- | :--- | :--- |
| **Amina Rahman** *(Head of Ops)* | "Balance alone won't cut it... repeat delinquency or disputed charges absolutely need human eyes." | **Duplicate work** | Wastes agent capacity; complex files get starved of high-judgment human focus. | **High** *(Validated via Live Chat)* |
| **Gareth Evans** *(Team Leader)* | "We need to know where they got stuck... context is the difference between a 2 and a 20-minute callback." | **Poor visibility** | inflates call handling times (AHT); leaves agents blind during automated hand-offs. | **High** *(Validated via Live Chat)* |
| **Daniel Okoye** *(Finance Director)* | "If reclaimed agent hours don't justify the investment independently, we're not proceeding—full stop." | **Financial credibility** | Immediate project veto and budget rejection if soft benefits are used to inflate the primary ROI model. | **High** *(Validated via Live Chat)* |
| **Gareth Evans** *(Team Leader)* | "A daily batched queue refresh is fine. Real-time alerts sound impressive, but they'd just create noise." | **Change resistance** | High agent distraction, disrupted daily workflows, and overall user rejection of the portal. | **High** *(Validated via Live Chat)* |
| **Daniel Okoye** *(Finance Director)* | "Show me the base case without it, then show me what happens if improved follow-up timing lifts collections by, say, 1-3%." | **Financial credibility** | Compliance failure; lacks transparent visibility for the board regarding proven vs. speculative returns. | **High** *(Validated via Live Chat)* |
| **Case Study Observation** | "...customers were often pushed into slow, repetitive contact journeys... wait on hold for basic balance views." | **Customer friction** | Damaged brand reputation, delayed case resolution, and artificially inflated call volumes. | **High** *(Historical Data)* |

---

## Step 3: Write JTBD statements

### JTBD table

| JTBD ID | Actor | Statement | Evidence link | Portal relevance | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **JTBD-01** | Finance Partner | **When** evaluating project viability, **I want to** separate hard operational cost-outs from speculative recovery gains into distinct scenarios, **so that** capital allocation is justified entirely by verifiable, audit-ready data. | Daniel Okoye Interview (`01-assumptions.csv` ID: A-01) | **High** (Sets the structural rules for the backend value engine) | **Critical** (Rank 1) |
| **JTBD-02** | Collections Agent | **When** picking up an abandoned portal session from the daily batch, **I want** instant visibility of the exact step where the user dropped out, **so that** I can skip initial discovery and execute a targeted, two-minute callback. | Gareth Evans Interview (`02-baseline-metrics.csv` ID: B-03) | **High** (Requires persistent UI state-logging on the frontend) | **High** (Rank 2) |
| **JTBD-03** | Operations Manager | **When** establishing automated portal triage logic for incoming accounts, **I want to** evaluate DPD thresholds, history, and open dispute flags, **so that** routine inquiries stay self-serve while complex cases bypass automation entirely. | Amina Rahman Interview (`02-baseline-metrics.csv` ID: B-01, B-02) | **High** (Requires backend parameter checks upon customer login) | **High** (Rank 3) |
| **JTBD-04** | Bank Customer | **When** my account falls into a delinquent status, **I want** a secure digital interface to confirm my outstanding liability and evaluate repayment options privately, **so that** I can resolve my debt quickly without enduring long phone queues. | Case Study Notes (Section: Customer Friction) | **High** (Core user interface capability) | **Medium** (Rank 4) |
| **JTBD-05** | Senior Team Leader | **When** managing my team's morning outreach schedule, **I want the backend to** generate a daily batched, intent-prioritized queue based on portal interaction levels, **so that** agents contact high-propensity accounts first without real-time notification noise. | Gareth Evans Interview (`03-opportunities.csv` ID: OP-05) | **Medium** (Governs the batch delivery layer to the internal CRM) | **Medium** (Rank 5) |

---

## Step 4: Top 3 justification

### 1. Financial Credibility Validation (JTBD-01)
* **Why it matters now:** Daniel Okoye has made it clear that Phase 1 will face an immediate budget veto if hard cost-out savings from reclaimed agent hours cannot independently prove a 12-month capital payback. We cannot rely on soft or guessed metrics to pass the baseline audit.
* **Which evidence supports it:** Daniel's direct live chat mandate: *"If reclaimed agent hours don't justify the investment independently, we're not proceeding—full stop."* Linked directly to asset `01-assumptions.csv` (ID: A-01).
* **How it should influence Phase 1:** The financial models (`04-roi-summary.csv`) must be strictly dual-scenario. All administrative time-savings must be programmatically derived from agent reconciliation averages, with speculative 1–3% recovery uplifts isolated cleanly into a separate sensitivity view.

### 2. Intent-Based Queue Prioritization & Session Logging (JTBD-02)
* **Why it matters now:** This capability bridges the structural gap between automated portal drop-outs and manual agent callbacks. Capturing the exact user state scales down agent investigation times from twenty minutes to two, reclaiming massive internal operational capacity.
* **Which evidence supports it:** Gareth notes: *"Context is the difference between a two-minute callback and a twenty-minute investigation."* He explicitly rejected real-time tracking in favor of an intent-prioritized batch queue. Linked directly to asset `02-baseline-metrics.csv` (ID: B-03).
* **How it should influence Phase 1:** Real-time alert infrastructure is completely cut from Phase 1 scope to protect agent focus. Instead, the portal backend must incorporate persistent state-logging at every stage of the user journey (Identity Verification ➔ Balance View ➔ Repayment Terms) and dump an intent-sorted, daily batched data file into the agent workflow.

### 3. Multi-Parameter Data Triage Rules (JTBD-03)
* **Why it matters now:** A simple, flat account-balance triage system will fail. It will accidentally trap complex account disputes or serial delinquencies within automated loops, causing severe customer friction and operational backlogs.
* **Which evidence supports it:** Amina's directive: *"Balance alone won't cut it... If someone's been through this cycle before or has an open dispute flag, I'd want them routed to agents..."* Linked directly to asset `02-baseline-metrics.csv` (IDs: B-01, B-02).
* **How it should influence Phase 1:** The future-state architecture cannot just be an external website interface; it must integrate a data-routing rules engine (**OP-05**). Upon customer login, the portal backend must evaluate multi-parameter operational criteria (such as Days Past Due thresholds and active dispute flags) to determine if the account is self-service eligible or must immediately drop into an agent's daily batch queue.