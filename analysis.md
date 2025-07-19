# 📘 Aave V2 Credit Scoring Model

## 🎯 Project Overview

This project assigns a **credit score (0–1000)** to wallets interacting with the Aave V2 DeFi protocol. The score is based entirely on a wallet’s transaction history—depositing, borrowing, repaying, redeeming, and liquidation activity. Higher scores indicate responsible and consistent behavior; lower scores reflect riskier profiles.

---

## 🧩 How It Works

### 📥 Input

* A JSON file containing Aave V2 transactions per wallet
* Each record includes:

  * `userWallet` (wallet address)
  * `timestamp` (UNIX)
  * `action` (e.g. deposit, borrow, repay)
  * `assetSymbol`, `amount`, `assetPriceUSD`

### 🔧 Feature Engineering

We extracted per-wallet features including:

* `total_deposit`, `total_borrow`, `total_repay`
* `repay_ratio`, `borrow_deposit_ratio`
* `num_liquidations`, `txn_freq`, `asset_diversity`, `avg_txn_size`

### 📐 Scoring Methods

We implemented three scoring strategies:

1. **Rule-Based Score** (Manual weights):

   * Encourages deposits, repayments, diverse and frequent transactions
   * Penalizes high borrow/deposit ratios and liquidations

2. **KMeans Clustering**:

   * Groups wallets into clusters based on behavior
   * Assigns scores by cluster

3. **Isolation Forest**:

   * Flags anomalous wallets (e.g. bots or risky usage)
   * Assigns low scores to outliers

### 📊 Output

The script produces a CSV file with columns:

```
wallet,credit_score,ml_credit_score_kmeans,ml_credit_score_iso
```

---

## ▶️ How to Run

```bash
python generate_credit_scores.py --input user-wallet-transactions.json --output wallet_scores_with_ml.csv
```

---

## 🔬 Extensibility Ideas

* Add wallet age or on-chain reputation
* Incorporate on-chain asset balances
* Use SHAP or LIME to interpret model-driven scores
* Streamlit dashboard for public score lookup

---

## 🧾 License

Open-source, research-only. Built for DeFi risk transparency.

Made with ❤️ for the future of trustless finance.
