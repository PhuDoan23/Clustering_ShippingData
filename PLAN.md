# HUTECH Student Research Conference 2026 - Sprint Plan

## Objective
Transform the existing `Ship_Performance_Dataset.csv` into an academic-grade dataset and submit a full paper to the **HUTECH Student Research Conference 2026** by the April 1st deadline.

**Current Date:** March 24, 2026
**Days Remaining:** 8 Days

---

## 📅 Daily Roadmap

### Phase 1: Dataset Modernization (Days 1)
**Day 1 (March 24): 2026 Industry Alignment**
- [ ] **Load existing baseline data** from `Ship_Performance_Dataset.csv`.
- [ ] **Add `Carbon_Intensity_Indicator` (CII):** Calculate estimated CII ratings based on baseline fuel consumption and ship parameters to reflect standard 2026 emission tracking.
- [ ] **Add `Fuel_Type`:** Incorporate 2026 green transition categories (e.g., *Methanol, Ammonia, LNG, HFO*), assigning appropriate probability distributions.
- [ ] **Inject Sensor Noise:** Add controlled Gaussian noise to engine telemetry and GPS data (e.g., `Speed_Over_Ground`) to simulate real-world IoT sensor imperfections.

### Phase 2: Rigorous Validation (Days 2-3)
**Day 2 (March 25): Rule-Based Logic Verification**
- [ ] **Physics Logic Pass:** Ensure strict, realistic relationships between `Engine_Power_kW`, `Speed_Over_Ground`, and `Operational_Cost_USD` (e.g., power vs speed cubic relationship).
- [ ] **Route Type Correlation:** Ensure `Route_Type` impacts weather conditions, speed patterns, and fuel efficiency logically.

**Day 3 (March 26): Statistical Testing for Realism**
- [ ] **Distribution Matching:** Run Kolmogorov-Smirnov (KS) tests to validate synthetic `Speed_Over_Ground` and fuel efficiency against real-world proxy distributions.
- [ ] **Correlation Matrix Heatmap:** Generate and save visual proof that variables interact correctly (e.g., high correlation between power and fuel consumption).

### Phase 3: FAIR Principles & Metadata (Day 4)
**Day 4 (March 27): Formatting and Documentation**
- [ ] **Export Multiple Formats:** Save final verified data as both `.csv` and `.parquet` (Interoperable).
- [ ] **Data Dictionary:** Create a detailed `metadata.json` documenting every column, unit of measurement, and synthesis logic.
- [ ] **Open Access Prep:** Define the repository structure for a Zenodo or IEEE Dataport release under a **CC-BY 4.0** license.

### Phase 4: Paper Writing & Submission (Days 5-8)
**Day 5 (March 28): Draft Initial Sections**
- [ ] Set up the paper template matching HUTECH formatting guidelines.
- [ ] Draft **Introduction**: Emphasize the lack of modern, open-source maritime datasets and the 2026 green transition.
- [ ] Draft **Methodology**: Explain synthetic generation, noise injection, and feature engineering (CII, Alternative Fuels).

**Day 6 (March 29): Results, Discussion & Visuals**
- [ ] Draft **Results**: Insert the Correlation Matrix and KS Test results to prove dataset validity.
- [ ] Draft **Discussion/Conclusion**: Explain the dataset's utility for ML researchers (e.g., predictive maintenance).
- [ ] **Format References**: Use Mendeley/Zotero to format citations correctly.

**Day 7 (March 30): Peer Review, Polish & DOI Setup**
- [ ] Self-review the paper against the HUTECH conference rubric.
- [ ] Upload the final dataset + `metadata.json` to Zenodo as a "Draft" to reserve the DOI.
- [ ] Insert the reserved DOI permanently into the research paper.

**Day 8 (March 31): Submission & Buffer**
- [ ] Final quality assurance check on all equations, figures, and formatting.
- [ ] **Submit Full Paper** to the HUTECH Conference portal.
- [ ] **Publish Zenodo Dataset** to make it publicly accessible.

---

## 📝 Next Steps
Whenever you are ready, let me know to start **Day 1: Dataset Modernization**. I will write the python scripts required to modernize `Ship_Performance_Dataset.csv`.
