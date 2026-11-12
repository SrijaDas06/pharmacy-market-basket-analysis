# Pharmacy Inventory Optimization Using Market Basket Analysis

## Overview

This project applies **Market Basket Analysis (MBA)** to prescription transaction data to identify medicines that frequently occur together. The objective is to uncover co-prescription patterns that can support pharmacy inventory planning and medicine availability.

The project explores association rule mining using two algorithms:

- **Apriori:** Identifies frequent itemsets and generates association rules.
- **FP-Growth:** Mines frequent patterns using an FP-tree-based approach.

The algorithms are compared using support, confidence and lift.

## Problem Statement

Pharmacies need to maintain adequate medicine stock while avoiding unnecessary overstocking. Analysing prescription transactions can reveal recurring medicine combinations and provide useful insights for inventory planning.

This project investigates how association rule mining can identify frequently occurring medicine combinations and help inform stock-management decisions.

## Objectives

- Identify frequently occurring medicine combinations in prescription transactions.
- Generate association rules for two-item and three-item medicine combinations.
- Evaluate associations using support, confidence and lift.
- Compare the results produced by Apriori and FP-Growth.
- Explore how the identified patterns could support pharmacy inventory planning.

## Methodology

1. **Data Collection:** Obtain prescription transaction data.
2. **Preprocessing:** Group medicines by transaction ID and transform transactions into a suitable format.
3. **Frequent Itemset Mining:** Apply Apriori and FP-Growth to identify frequent medicine combinations.
4. **Association Rule Generation:** Generate rules using support, confidence and lift.
5. **Comparison:** Compare the algorithms across the analysed prescription categories.
6. **Interpretation:** Examine recurring medicine combinations and their potential relevance to inventory management.

## Apriori Implementation

The provided Apriori implementation uses the following parameters:

| Parameter | Value |
|---|---:|
| Minimum support | 30% |
| Minimum confidence | 50% |
| Itemset sizes | 2-item and 3-item |

The implementation uses `mlxtend` for transaction encoding, frequent itemset mining and association rule generation.

## Evaluation Metrics

- **Support:** Indicates how frequently a medicine combination appears in the transactions.
- **Confidence:** Measures how frequently the consequent appears when the antecedent occurs.
- **Lift:** Measures the strength of an association relative to independent occurrence.

A lift greater than 1 indicates a positive association in the analysed dataset.

## Key Findings

The research compares Apriori and FP-Growth across symptom-wise prescription categories.

Examples reported in the research include:

- Paracetamol and Tramadol: confidence of 1.00 and lift of 3.20.
- Syrup Granocyf and Nasoclear nasal drops: confidence of 1.00 and lift of 2.46.
- Coldvan and Lasix 40: confidence of 0.91 and lift of 1.21 in the reported pressure-related analysis.

The findings illustrate how recurring transaction patterns can provide information for pharmacy stock planning.

**Note:** These are associations observed in the analysed prescription data, not medical recommendations or evidence that medicines should be prescribed together.

## Technologies Used

- Python
- Pandas
- Mlxtend
- Apriori Algorithm
- FP-Growth Algorithm
- Association Rule Mining
- Jupyter Notebook

## Repository Structure

```text
Pharmacy-Market-Basket-Analysis/
│
├── README.md
├── requirements.txt
│
├── data/
│   └── README.md
│
├── notebooks/
│   └── market_basket_analysis.ipynb
│
├── src/
│   ├── apriori_analysis.py
│   ├── fpgrowth_analysis.py
│   └── preprocessing.py
│
├── outputs/
│   └── association_rules.csv
│
├── visualizations/
│   └── association_rules.png
│
└── reports/
    └── research_paper.pdf
```

## Potential Applications

- Identifying frequently associated medicines.
- Supporting inventory prioritisation.
- Informing stock replenishment decisions.
- Understanding recurring prescription transaction patterns.

## Research Work

This project is associated with the research study:

**"Optimizing Pharmacy Business and Inventory Management: A Comprehensive Study through Market Basket Analysis based on Co-Prescription Patterns using Data Analytics."**

The study examines Apriori and FP-Growth for pharmacy inventory-management applications.

## Disclaimer

This project is intended for academic research and inventory-analysis purposes only. Association rules identify patterns in historical transaction data and must not be interpreted as clinical prescribing recommendations.
