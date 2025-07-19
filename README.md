💳 Aave V2 Wallet Credit Scoring
📌 What This Project Does
This project gives a credit score (from 0 to 1000) to wallets that interact with the Aave V2 DeFi protocol. The score is based only on each wallet's past activity like deposits, borrows, repayments, and liquidations.

High score = Responsible and consistent usage

Low score = Risky, bot-like, or unusual behavior

📂 Input File
The input is a JSON file with wallet transactions. Each record includes:

userWallet: Wallet address

timestamp: Time of transaction

action: Type of action (e.g., deposit, borrow, repay)

assetSymbol, amount, assetPriceUSD: Token info

🧠 How the Score is Calculated
We calculate useful features from each wallet’s history, such as:

Total deposit, borrow, and repay amounts

Repay ratio and borrow-to-deposit ratio

Number of liquidations

Frequency, size, and diversity of transactions

Three Scoring Methods:
Rule-Based:

Rewards good behavior (deposits, repayments, variety)

Penalizes risk (high borrow ratios, liquidations)

KMeans Clustering:

Groups wallets based on behavior

Assigns score based on cluster

Isolation Forest:

Detects outliers

Gives lower scores to wallets that act differently from most others

📤 Output File
The script outputs a CSV file like this:

Copy
Edit
wallet,credit_score,ml_credit_score_kmeans,ml_credit_score_iso
Each column represents a score using different methods.

▶️ How to Run
bash
Copy
Edit
python generate_credit_scores.py --input user-wallet-transactions.json --output wallet_scores_with_ml.csv
Make sure you have installed Python and required packages like pandas, numpy, sklearn, etc.

💡 Ideas for Improvement
Use wallet age or on-chain token balances

Add a dashboard (e.g., with Streamlit)

Explain ML scores using SHAP or LIME

Label good/bad wallets using known addresses

📜 License
This is for research and educational purposes only.
Built to help understand risk in decentralized finance (DeFi).

