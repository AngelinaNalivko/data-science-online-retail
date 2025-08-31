# Market Basket Analysis Using the Apriori Algorithm

Association rule mining on the UCI **Online Retail** dataset with per‑country insights (UK, France, Germany, Ireland), data cleaning pipeline, Apriori mining, and heatmap visualizations.

## Project overview

This repository contains a data science project focused on Market Basket Analysis (MBA) using the Apriori algorithm. The goal is to discover meaningful product associations in online retail transactions and compare country‑specific shopping patterns across the United Kingdom, France, Germany, and Ireland.

## Key Objectives

- Clean and standardize noisy retail data (missing values, typos, inconsistent product names).
- Build market‑basket transactions and mine frequent itemsets and association rules with Apriori.
- Generate per‑country insights to support marketing, cross‑selling, and merchandising decisions.

## Dataset

- **Source:** UCI Machine Learning Repository — *Online Retail* (Dec 2010 – Dec 2011).
- **Schema (excerpt):** `InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country`.  
- **Notes:** Contains >500k rows; includes canceled invoices, duplicates, and missing values (notably in `CustomerID`, `Description`). 

## Methodology (Apriori)

- **Transaction building:** group by `InvoiceNo` → list of unique product descriptions per invoice.  
- **One‑hot encoding:** `TransactionEncoder` (mlxtend) → sparse boolean matrix.  
- **Frequent itemsets:** `apriori(min_support=0.02)` (example threshold).  
- **Rules:** `association_rules(min_confidence=0.5)`, with de‑duplication of semantically identical rules.  
- **Per‑country mining:** run the same pipeline for UK, France, Germany, Ireland.

> **Example rule (France):**  
> `(acapulco mat recycled red, acapulco mat recycled turquoise) → acapulco lavender mat recycled` with **lift ≈ 34.84**.

## Visualizations

- **Heatmaps** of rules: antecedents (y‑axis) × consequents (x‑axis), colored by lift.  
- Separate heatmaps per country for quick pattern scanning and comparison.

## Insights (Country Snapshot)

- **United Kingdom:** large rule volume; coordinated **home décor** (e.g., t‑light holders, wicker hearts).  
- **France:** **colorful / eco‑friendly** sets (e.g., *acapulco* recycled mats) bought together.  
- **Germany:** more **functional/DIY** items (e.g., jam‑making sets + labels).  
- **Ireland:** **festive/seasonal** decorations (e.g., “birthday bunting” variants).
