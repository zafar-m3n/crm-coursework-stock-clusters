# CRM Coursework – Grouping S&P 500 Stocks

Coursework for 6BUIS017W (CRM & CM with Business Intelligence). The notebook groups S&P 500 shares in two ways: by risk and return (mean weekly return and weekly beta) and by trading activity (an adapted Recency, Frequency, Monetary model). Each is clustered with Ward and K-means.

## Key details

- **Share list:** Wikipedia "List of S&P 500 companies", page version from 20 November 2026 (revision 1384572480)
- **Price data:** yfinance, daily, 1 January 2021 – 1 January 2025 (end date excluded)
- **Benchmark:** S&P 500 index (^GSPC)
- **Observation date for RFM:** 31 December 2024
- **Shares:** 503 on the list, 17 excluded (see `outputs/exclusion_log.csv`), 486 analysed
- **Clusters chosen:** risk and return k = 4, trading activity k = 3
- **K-means:** random_state = 42, n_init = 50

## How to run

1. Install Python 3.12, then run:

   ```
   python -m venv .venv
   .venv\Scripts\activate
   pip install -r requirements.txt
   ```

2. Open `CRM Assignment - Grouping S&P 500 Stocks.ipynb` and run all cells.

The notebook loads the saved data in `data/raw/`, so the results match exactly. If those files are deleted, it downloads everything again. Yahoo's adjusted prices can change slightly over time, so a fresh download may give very slightly different numbers.

To run it in Google Colab, start with:

```
!git clone https://github.com/zafar-m3n/crm-coursework-stock-clusters.git
%cd crm-coursework-stock-clusters
```

## What's in the repo

| Folder / file | Contents |
|---|---|
| `CRM Assignment - Grouping S&P 500 Stocks.ipynb` | All code, with outputs |
| `requirements.txt` | Package versions used |
| `data/raw/` | Saved snapshot: share list, daily adjusted close, close and volume |
| `data/processed/` | Weekly prices and returns, feature tables |
| `outputs/exclusion_log.csv` | Shares left out and why |
| `outputs/cluster_assignments.csv` | One row per share: features and all cluster labels |
| `outputs/cluster_profiles_*.csv` | Cluster profiles in original units |
| `outputs/*_k_selection.csv` | Silhouette, inertia and cluster sizes for k = 2 to 8 |
| `outputs/rfm_correlations.csv`, `outputs/sector_composition.csv` | Sensitivity and sector tables |
| `outputs/figures/` | All charts |
