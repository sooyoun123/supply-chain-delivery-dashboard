# 🚚 Global Supply Chain Delivery Performance Dashboard

Analyzing on-time delivery patterns and root causes across regions, countries, and shipping modes.

**Tools:** Power BI, Power Query, DAX
**Data:** Kaggle — DataCo Smart Supply Chain Dataset (~180,000 orders)
**GitHub:** https://github.com/sooyoun123/supply-chain-delivery-dashboard

---

## 📌 About

This project analyzes global order and delivery data to identify patterns in late deliveries across regions, countries, and shipping modes — and digs into *why* those patterns exist rather than just reporting the numbers.

## 🔧 Process

1. **Data Cleaning (Power Query)**
   - Loaded raw CSV (180K+ rows, 53 columns) into Power BI
   - Fixed file encoding issues (Western European encoding)
   - Renamed ambiguous columns (`Late_delivery_risk` → `IsLate`) for clarity
   - Created calculated columns: `Delay Days`, `IsLate`, `Monthly Order` (month-start date for trend analysis)

2. **KPI Design (DAX)**
   - `On-Time Delivery Rate`
   - `Total Sales`
   - `Avg Delay Days` (all orders / late orders only)
   - `Late Delivery Count`

3. **Visualization**
   - Page 1 — Overview: KPI cards, Top 5 delayed countries, regional delay comparison, yearly trend
   - Page 2 — Root Cause: Shipping mode analysis

## 💡 Key Insights

- **Overall on-time delivery rate is only 45%**, with average delays of 1.6 days among late orders.
- **First Class shipping shows the lowest on-time rate (~10%)** — but this is not a performance problem. It reflects a **1-day scheduled delivery target**, compared to 4 days for Standard Class. A tighter target makes any small delay register as "late."
  → This is a good example of why raw metrics need structural context before drawing conclusions.
- Regional and country-level delay rates are relatively uniform (54–58%), suggesting delays are not concentrated in specific geographies within this dataset.

## ⚠️ Limitations & Lessons Learned

- Country names in the raw dataset are recorded in Spanish (e.g., "Alemania" = Germany, "Estados Unidos" = United States). These were kept as-is in this version.
  → **Lesson: always check categorical/text columns for language or locale issues before starting analysis.**
- This dataset does not include process-level timestamps (e.g., customs clearance, supplier lead time, warehouse dispatch), so root-cause analysis is limited to structural/statistical patterns rather than true operational causes.
  → With richer data, root cause analysis would involve breaking the fulfillment process into stages (order → inventory check → supplier → customs → shipping) and comparing stage-level lead times between delayed and on-time orders.

## 🔗 Links

- GitHub Repo: https://github.com/sooyoun123/supply-chain-delivery-dashboard
- Dataset: [Kaggle - DataCo Smart Supply Chain Dataset](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis)
