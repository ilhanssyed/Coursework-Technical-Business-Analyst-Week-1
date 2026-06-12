# Discovery Brief: Legacy-Trust Bank Modernization

## 1. Problem summary

Legacy-Trust Bank’s debt recovery operations are bottlenecked by an unintegrated, 20-year-old legacy collections database supplemented by fragmented spreadsheets and manual email trails. Over 50 full-time agents are currently overwhelmed managing a pool of more than 100,000 delinquent accounts within a single, unsegmented queue. This lack of automation forces high-complexity cases and straightforward balance verifications into the exact same manual workflow. Operationally, this causes severe duplicate outreach, fragmented status tracking, and massive administrative overhead. Financially, these delayed actions and inconsistent follow-ups result in an estimated 15% revenue leakage across the account portfolio.

## 2. Stakeholder overview

Complete a short table like the one below.

| Stakeholder group | What they care about | How success is measured | Main worry | Evidence they will trust |
|---|---|---|---|---|
| Operations leadership | TODO | TODO | TODO | TODO |
| Team leaders and agents | TODO | TODO | TODO | TODO |
| Finance | TODO | TODO | TODO | TODO |
| Product and delivery | TODO | TODO | TODO | TODO |
| Customers | TODO | TODO | TODO | TODO |

## 3. Discovery questions

Write 5-7 questions that point toward evidence.

Starter examples:
- Which steps in debt recovery are high-volume and rules-driven enough for self-service?
- Where do spreadsheets and manual handoffs create duplicate work?
- Which baseline metrics best show operational waste and revenue leakage?

## 4. Traceability starter

Create a first-pass table.

| Stakeholder concern | Likely process area affected | Possible metric or evidence source | Likely deliverable |
|---|---|---|---|
| TODO | TODO | TODO | TODO |

## 5. Final problem statement

End with a concise problem statement in your own words.

> Tip: if your statement still sounds like 'the bank needs digital transformation,' it is too broad.

# Discovery Brief: Legacy-Trust Bank Modernization

## 1. Problem summary
Legacy-Trust Bank’s debt recovery is stuck using an unintegrated, 20-year-old collections database, messy local spreadsheets, and manual email trails. While account volumes have scaled across personal loans, credit cards, and auto finance, our operations haven't changed. Right now, 50 full-time agents are drowning in a pool of over 100,000 delinquent accounts sitting in a single, unsegmented queue. Because there's no automation, simple balance checks and highly complex cases are thrown into the exact same manual workflow. This wastes agent capacity on routine tasks, causes duplicate customer outreach, and leads to an estimated 15% revenue leakage across the portfolio due to delayed, inconsistent follow-ups.

---

## 2. Stakeholder overview

| Stakeholder group | What they care about | How success is measured | Main worry | Evidence they will trust |
| :--- | :--- | :--- | :--- | :--- |
| **Operations Leadership** *(Amina)* | Stopping duplicate agent work and separating simple tasks from complex cases to free up team capacity. | • Fewer missed customer follow-ups<br>• Lower Average Handling Time (AHT) | The portal fails to handle edge cases cleanly, dumping messy exceptions back onto agents. | • Simple As-Is process maps showing current queue blocks<br>• Time-savings math tied directly to agent tasks |
| **Team Leaders & Agents** *(Gareth)* | Process consistency across the 50+ agents and real Ground conditions matching our system data. | • Significant drop in duplicate customer calls<br>• Real-time, centralized account updates | High-level automation that looks great on paper but pushes broken hand-offs onto live agents. | • Honest, unvarnished As-Is documentation<br>• Clear process boundaries showing where automated loops end |
| **Finance** *(Daniel)* | Keeping costs down, staying compliant, and seeing bulletproof risk/return numbers. | • Clear 12-month capital payback<br>• Measurable reduction in the 15% value leakage | Blurry financial guesses that blend hard time-savings with speculative revenue uplifts. | • Clean operational baselines derived from actual data files<br>• Tight sensitivity testing on the financial models |
| **Product & Delivery** *(Priya)* | Building a solid, workable backlog and validating technical feasibility before writing code. | • 100% technical feasibility validation before building<br>• A highly traceable prototype backlog | Moving into delivery on vague requirements, causing devs to hit a brick wall mid-sprint. | • Data schemas mapping manual pain points straight to tech opportunities (OP-01 to OP-05) |
| **Customers** *(Delinquent Pool)* | Fast, private access to balance details and low-friction, respectful repayment options. | • Way shorter phone queue hold times<br>• Faster self-serve resolution speed | Being locked out of digital channels and forced onto slow, repetitive phone queues for minor updates. | **DISCOVERY GAP:** Needs are currently inferred from operational symptoms. No direct customer data exists yet. |

---

## 3. Discovery questions

* **Self-Service Suitability:** Which specific parts of the debt recovery lifecycle are high-volume and rules-driven enough to hand over to a customer self-service portal?
* **Process Failure Points:** Where exactly do manual file swaps and local spreadsheet tracking cause agents to double-call customers or miss scheduled follow-ups?
* **Value Case Baselines:** What are the exact baseline figures—specifically AHT and daily reconciliation hours—needed to prove hard operational cost savings to Daniel?
* **Technical Roadblocks:** What integration limits within the 20-year-old legacy database could stop the new portal from writing real-time status updates?
* **Operational Trust:** What clear boundaries do we need to set between automated portal triggers and live agent queues to get Gareth's team to actually trust the system?

---

## 4. Traceability starter

| Stakeholder concern | Likely process area affected | Possible metric or evidence source | Likely deliverable |
| :--- | :--- | :--- | :--- |
| **Amina:** 50 agents buried in unsegmented queue capacity. | Current-state account triaging and routing. | `02-baseline-metrics.csv` (IDs: B-01, B-02) | As-Is Process Map (Camunda) showing queue blocks. |
| **Daniel:** 15% recovery leakage from poor follow-ups. | Sequential account outreach and tracking. | `02-baseline-metrics.csv` (ID: B-03) | ROI Summary & Sensitivity Model (`04-roi-summary.csv`). |
| **Gareth:** Messy data reconciliations and tool distrust. | Internal agent account updating workflow. | `02-baseline-metrics.csv` (ID: B-04) | Defined To-Be Process Boundary Diagrams. |
| **Priya:** Strategy-to-engineering delivery gaps. | Technical requirement translation. | `01-assumptions.csv` (IDs: A-01 to A-04) | Traceable Prototype Backlog with mapped data schemas. |
| **Project Risk:** Complete lack of customer validation. | Customer portal authentication and UI. | **DISCOVERY GAP** (No current VoC source) | Risk Log Escalation & Phase 2 Customer Validation Plan. |

---

## 5. Final problem statement
Legacy-Trust Bank’s debt recovery framework cannot scale under a volume of 100,000 delinquent accounts because the operation relies entirely on unsegmented, spreadsheet-driven workflows. By dumping low-complexity balance verification tasks and high-value, complex cases into the exact same manual queue managed by only 50 agents, the bank is causing massive operational duplication, severe delays in customer follow-up, and a 15% revenue leakage. We cannot scale capacity or protect the bottom line without building an automated routing infrastructure and a secure self-service layer that splits routine inquiries away from high-judgment human recovery workflows.