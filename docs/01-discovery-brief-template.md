# Discovery Brief: Legacy-Trust Bank Modernization

## 1. Problem summary
Legacy-Trust Bank’s debt recovery operation is severely constrained by an unintegrated, 20-year-old collections database, local Excel tracking sheets, and manual email trails. While delinquency volumes have scaled to **over 100,000 accounts** across personal loans, credit cards, and auto finance, our operational workflows have not evolved. Today, 50 full-time agents operate out of a single, unsegmented queue. Straightforward, routine inquiries and highly complex cases are tangled in the exact same manual workflow. This structure misallocates limited agent capacity on administrative tasks, triggers duplicate customer outreach, and drives a **14% missed follow-up rate (FA-06)** on broken payment promises. The resulting delays contribute directly to an estimated **15% value leakage** against our **£8,000,000 monthly recovery baseline (FA-09)**.

---

## 2. Stakeholder overview

| Stakeholder group | What they care about | How success is measured | Main worry | Evidence they will trust |
| :--- | :--- | :--- | :--- | :--- |
| **Operations Leadership** *(Amina)* | Eliminating duplicate agent efforts and separating routine interactions from complex cases to free up judgment capacity. | • Elimination of manual reconciliation waste<br>• Lower Average Handling Time (AHT) from 18 to 10 mins | The portal handles exceptions poorly, dropping messy account data back onto live agent queues. | • Clear As-Is maps exposing current queue blocks<br>• Time-savings calculations tied directly to agent tasks |
| **Team Leaders & Agents** *(Gareth)* | Field execution matching official database records; ensuring data consistency across all 50+ agents. | • Elimination of duplicate customer calls<br>• A unified view of account state upon logging in | High-level automation that looks optimized on paper but pushes broken hand-offs onto the floor. | • Honest documentation of daily spreadsheet dependencies<br>• Clear process boundaries for automated loops |
| **Finance** *(Daniel)* | Controlling operational costs, ensuring legal compliance, and reviewing bulletproof risk/return data. | • Clear 12-month capital payback<br>• Verifiable operational cost reductions | Blurry financial models that mask soft, speculative revenue uplifts inside primary cost-out calculations. | • Transparent, dual-scenario value models<br>• Strict sensitivity testing separating hard and soft savings |
| **Product & Delivery** *(Priya)* | Creating a highly traceable, structured backlog and validating technical feasibility before development. | • 100% requirements traceability<br>• A buildable prototype backlog | Moving into development on vague requirements, causing engineers to stall mid-sprint. | • Data schemas linking manual pain points straight to tech opportunities (OP-01 to OP-05) |
| **Customers** *(Delinquent Pool)* | Secure, private access to outstanding liability details and low-friction options to resolve accounts. | • Shorter phone queue hold times<br>• Fast, unassisted self-service speed | Being locked out of digital channels and forced onto slow, repetitive phone queues for minor balance checks. | **DISCOVERY GAP:** Customer needs are currently inferred from operational data. No direct customer voice metrics exist yet. |

---

## 3. Discovery questions

* **Self-Service Suitability:** How can we safely leverage our **38% straightforward case share (FA-03)** to migrate volume out of agent call queues and into a secure self-service track?
* **Process Failure Points:** Why does the legacy architecture treat payment promises identically to payment confirmations (**SN-126**), and where exactly do spreadsheet updates cause agents to act on stale data?
* **Value Case Baselines:** How can we precisely measure the administrative hours lost per day to local spreadsheet reconciliations (**B-04**) using the `spreadsheet_reconcile` activity stamps from the operational log?
* **Technical Roadblocks:** What backend integration limits within the 20-year-old database prevent it from enforcing scheduled callback dates, causing files to stall indefinitely in 'pending' status (**SN-118**)?
* **Operational Trust:** How can we configure the portal backend to validate risk bands (extracting `high` risk accounts as `ineligible`) to prevent complex exception cases from destabilizing automated channels?

---

## 4. Traceability starter

| Stakeholder concern | Likely process area affected | Possible metric or evidence source | Likely deliverable |
| :--- | :--- | :--- | :--- |
| **Amina:** Straightforward and complex cases tangled in the same manual flow. | Account triaging, routing, and segmentation layer. | `finance_assumptions.csv` (ID: FA-03 - 38% case share) | As-Is Process Map highlighting unsegmented queue blocks. |
| **Daniel:** Value leakage driven by delayed actions and inconsistent tracking. | Sequential account outreach and follow-up tracking. | `finance_assumptions.csv` (ID: FA-06 - 14% missed follow-up) | Dual-Scenario ROI Summary & Sensitivity Model. |
| **Gareth:** Agents spending time manually running `spreadsheet_reconcile` tasks. | Internal agent morning prep and account verification. | `recovery_activity_tracker.csv` (`spreadsheet_reconcile` activity logs) | Defined To-Be Process Boundary Diagrams. |
| **Priya:** Strategy-to-engineering delivery gaps and backlog alignment. | Technical requirement and data flow translation. | `finance_assumptions.csv` (IDs: FA-10, FA-11 - Dev Costs) | Traceable Prototype Backlog with mapped opportunity schemas. |
| **Project Risk:** Customer needs are entirely inferred from operational symptoms. | Customer portal authentication and interface design. | **DISCOVERY GAP** (No direct source in dataset) | Risk Log Escalation & Phase 2 Customer Validation Plan. |

---

## 5. Final problem statement
Legacy-Trust Bank’s debt recovery framework cannot scale under a volume of over 100,000 delinquent accounts because the operation relies entirely on unsegmented, manual workflows. By throwing routine balance verification tasks—which account for **38% of our entire case share (FA-03)**—and high-value, complex files into the exact same manual queue managed by only 50 agents, the bank causes massive operational duplication. Agents are forced to lose hours to manual `spreadsheet_reconcile` work before acting, leading to an average handling time of **18 minutes per case (FA-04)** and a **14% missed follow-up rate (FA-06)** when payment promises fail to clear silently (**SN-126**). We cannot stabilize capacity or protect the bottom line without building an automated backend routing framework and a secure customer self-service layer that permanently decouples routine inquiries from high-judgment human recovery workflows.