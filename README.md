# 📊 SaaS Revenue & Churn Intelligence Dashboard

## 🎯 The Challenge
A subscription-based business needed a way to track real-time financial health, but the raw data was trapped in disorganized, fragmented spreadsheets. The main obstacles blocking operational visibility included:

* **Data Discrepancy:** Inconsistent data types—specifically critical subscription dates stored entirely as unformatted text—prevented accurate timeline analysis.
* **Complex Temporal Logic:** The team lacked a way to calculate **Active Monthly Recurring Revenue (MRR)** dynamically across moving timelines, which required accounting for subscriptions that started in the past but had not yet reached their expiration date.
* **Manual Reporting Bottlenecks:** Stakeholders had no scalable way to visualize growth trends or segment historical performance without relying on brittle, slow manual calculations.

---

## 💡 The Solution
I engineered a robust, end-to-end Business Intelligence solution utilizing the full Power BI stack to turn raw transactional logs into structured analytics assets.

### ⚙️ ETL & Data Engineering
* **Power Query Pipeline:** Engineered automated transformation steps to scrub messy source data, enforce strict downstream database schemas, and eliminate data type formatting anomalies.
* **Time Intelligence Engine:** Generated a dedicated, dynamic **Calendar Table** inside the data engine to unlock advanced time-series analysis and seamless period-over-period tracking.

### 📐 Relational Data Modeling
* Designed and deployed an optimized **Star Schema** architectural framework.
* Established rigid one-to-many operational relationships between central `Subscription` fact tables and independent `Customer` and `Date` dimension blocks to preserve data integrity and prevent cross-filtering inflation errors.

  ### 🧮 Advanced DAX Architecture
* Authored performant, scalable measures to compute **Running Total Revenue** and **Active Subscriptions** over rolling windows.
* Utilized targeted `CALCULATE`, `FILTER`, and context-modification logic to evaluate fluid start-and-end subscription states on the fly:

$$\text{Active Subscriptions} = \text{CALCULATE}(\text{Count},\text{Filter}(\text{Start Date} \le \text{Max Date} \land \text{End Date} \ge \text{Max Date}))$$

### 🎨 Interactive UI/UX Design
* Formulated a high-fidelity, stakeholder-ready executive control center.
* Integrated deep drill-through tracking, structural regional slicing, and customer profile categorization (**Enterprise vs. SMB**) to let users easily isolate distinct cohorts.

---

## 📈 The Impact
* ⚡ **Instant Insights:** Slashed the time required to compile and calculate monthly churn metrics from **hours of manual spreadsheet linking down to a split-second, automated dashboard refresh**.
* 💰 **Revenue Transparency:** Provided clear visual clarity over the business's "staircase" recurring growth effect, instantly surfacing the fact that **Enterprise clients served as the primary revenue locomotive, generating 94% of total corporate MRR**.
* 🔒 **100% Data Accuracy:** Completely eliminated generic `"Blank"` data rendering traps by enforcing structured physical relationships at the core data layer, ensuring perfect reconciliation between base database inputs and frontend visual reports.
