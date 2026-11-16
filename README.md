# Pharmacy Inventory Optimization using Market Basket Analysis

Co-prescription pattern mining with **Apriori** and **FP-Growth** to support medicine stock decisions in a pharmacy.

> Companion code for the paper *"Optimizing Pharmacy Business and Inventory Management: A comprehensive study through Market Basket Analysis based on Co-Prescription Patterns using Data Analytics"*
> Srija Das, Tamajit Pal, Tamali Khan, Bidisha Bhabani, Tanaya Das, Radhakrishna Jana. CSE, JIS University, Kolkata, India.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/<your-username>/<your-repo>/blob/main/Pharmacy_MBA_Apriori_FPGrowth.ipynb)

---

## Overview

Stockouts and overstocking are the two largest inventory problems in retail, and pharmacies feel both acutely. This project treats each prescription as a "basket" of medicines and mines association rules to find which medicines are prescribed together. Medicines that co-occur with high support, confidence and lift are candidates for guaranteed stock and bundled placement.

Prescriptions are grouped by symptom category:

| Symptom group | Transactions | Unique medicines |
|---|---|---|
| Fever, cough, headache and body pain | 32 | 19 |
| Pressure (blood pressure) | 20 | 33 |
| Hypertension | 20 | 32 |
| Gastric, vomiting and food poisoning | 30 | 39 |

## Pipeline

1. **Load** the cleaned transactions from each workbook (`dummy data` sheet).
2. **Encode** each basket as a one-hot matrix (`TransactionEncoder`).
3. **Mine** frequent itemsets with Apriori and FP-Growth (`mlxtend`).
4. **Generate** association rules and compute support, confidence and lift.
5. **Split** rules into 2-itemset and 3-itemset tables (paper Tables 3-8).
6. **Compare** the two algorithms (rule agreement, averaged runtime).
7. **Visualise** and **export** results to Excel.

Default thresholds (they reproduce the paper's tables):

| Parameter | Value |
|---|---|
| `MIN_SUPPORT` | 0.30 |
| `MIN_CONFIDENCE` | 0.50 |

## Repository structure

```
.
├── Pharmacy_MBA_Apriori_FPGrowth.ipynb   # Full analysis notebook (Google Colab)
├── data/
│   ├── fever_cough_headache_bodypain_Apriori___Fp_final.xlsx
│   ├── pressure_Apriori___FP_final.xlsx
│   ├── hypertension_Apriori___FP_final.xlsx
│   ├── Gastric__vomiting__food_Apriori__FP_final.xlsx
│   └── all_data_with_each_med_frequency__2_.xlsx   # optional, used for Fig. 1-2
└── README.md
```

## Getting started

### Google Colab (recommended)

1. Click the **Open in Colab** badge above.
2. Run all cells (`Runtime` → `Run all`).
3. When prompted, upload the `.xlsx` files from `data/`.

### Local

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
pip install mlxtend pandas numpy matplotlib openpyxl jupyter
jupyter notebook Pharmacy_MBA_Apriori_FPGrowth.ipynb
```

Copy the `.xlsx` files into the notebook's working directory, since the upload cell only works inside Colab.

## Data

- Source: prescriptions from an Indian pharmacy, obtained from Kaggle (see the paper, Phase I).
- Each workbook contains the raw prescriptions (`original data`), the cleaned transactions (`dummy data`, the notebook's input) and the originally reported Apriori and FP-Growth outputs.
- Medicine names were normalised from free-text prescriptions (for example `TAB. RANITIDINE 150 MG BD` became `RANITIDINE`). That normalisation was done outside the notebook, so the notebook starts from the cleaned sheets.

## Selected results

Highest-signal 2-itemset rules (identical under both algorithms):

| Symptom group | Rule | Support | Confidence | Lift |
|---|---|---|---|---|
| Fever, cough, body pain | Syrup Granocyf → Nasoclear Nasal Drops | 0.34 | 1.00 | 2.46 |
| Fever, cough, body pain | Paracetamol ↔ Tramadol | 0.31 | 1.00 | 3.20 |
| Pressure | Rantac 150 → Lasix 40 | 0.60 | 0.86 | 1.14 |
| Pressure | Coldvan → Lasix 40 | 0.50 | 0.91 | 1.21 |
| Hypertension | Pantoprazole → Furosemide | 0.35 | 0.87 | 1.46 |
| Gastric, vomiting, food poisoning | Lasix → Amlodipine | 0.53 | 1.00 | 1.50 |

The notebook also produces the full rule tables, per-rule plots and a stock-priority ranking per symptom group, and exports everything to `MBA_results.xlsx`.

## Limitations

- **Small datasets.** Each group has only 20-32 transactions, so a support of 0.30 corresponds to 6-10 prescriptions. Results are illustrative, not statistically robust.
- **Algorithm comparison.** Apriori and FP-Growth return identical rules at identical thresholds, as expected. On data this small, runtime differences (roughly 3-5 ms) are noise, so no speed or scalability conclusion should be drawn from this repository.
- **Association is not causation.** Co-prescription reflects clinical practice and prescriber habits, not demand forecasts. Rules should inform, not replace, stock-level planning.

## Future work

- Larger, multi-pharmacy transaction data
- Stock-out prediction using transaction history and live inventory levels
- Region-level demand and prevalent-disease analysis

## Citation

```bibtex
@article{das_pharmacy_mba,
  title   = {Optimizing Pharmacy Business and Inventory Management: A comprehensive study through Market Basket Analysis based on Co-Prescription Patterns using Data Analytics},
  author  = {Das, Srija and Pal, Tamajit and Khan, Tamali and Bhabani, Bidisha and Das, Tanaya and Jana, Radhakrishna},
  journal = {<journal / venue>},
  year    = {<year>},
  doi     = {<doi>}
}
```

## Authors

Srija Das, Tamajit Pal, Tamali Khan, Bidisha Bhabani, Tanaya Das, Radhakrishna Jana
Department of CSE, JIS University, Kolkata, West Bengal, India

Correspondence: bidisha035810@gmail.com

## License

<!-- Choose one, e.g. MIT, and add a LICENSE file. -->
Released under the MIT License. See `LICENSE`.
