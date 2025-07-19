# 💳 Aave V2 Wallet Credit Scoring

## 📌 What This Project Does

This project gives a **credit score (from 0 to 1000)** to wallets that interact with the Aave V2 DeFi protocol. The score is based only on each wallet's past activity like deposits, borrows, repayments, and liquidations.

- **High score** = Responsible and consistent usage  
- **Low score** = Risky, bot-like, or unusual behavior

---

## 📂 Input File

The input is a JSON file with wallet transactions. Each record includes:

- `userWallet`: Wallet address  
- `timestamp`: Time of transaction  
- `action`: Type of action (e.g., deposit, borrow, repay)  
- `assetSymbol`, `amount`, `assetPriceUSD`: Token info  

---

## 🧠 How the Score is Calculated

We calculate useful features from each wallet’s history, such as:

- Total deposit, borrow, and repay amounts  
- Repay ratio and borrow-to-deposit ratio  
- Number of liquidations  
- Frequency, size, and diversity of transactions  

### Three Scoring Methods

1. **Rule-Based**  
   - Rewards good behavior (deposits, repayments, variety)  
   - Penalizes risk (high borrow ratios, liquidations)

2. **KMeans Clustering**  
   - Groups wallets based on behavior  
   - Assigns score based on cluster

3. **Isolation Forest**  
   - Detects outliers  
   - Gives lower scores to wallets that act differently from most others

---

## 📤 Output File

The script outputs a CSV file like this:

