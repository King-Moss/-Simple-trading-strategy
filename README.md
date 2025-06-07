# -Simple-trading-strategy
A simple moving average crossover strategy using Facebook stock data to evaluate profitability over 1.5 years for short term traders.
# 📊 Simple Trading Strategy using Facebook and Microsoft Stock Data

This project explores a basic moving average crossover trading strategy using historical stock data for Facebook and Microsoft.

---

## 🔍 Project Description

I gathered 5 years' worth of Facebook and Microsoft stock data (from 2021 to June 2025) using an alternative method since I had exceeded my Yahoo Finance data limit. The dataset included essential features like Open, High, Low, Close, and Volume.

Here's what I did:

1. **Previewed the Data**: Printed the full dataset and the last five rows to inspect.
2. **Sliced the Data**: Reduced it to only the last **1 year and 6 months** for focused analysis.
3. **Created Technical Indicators**:
   - **MA10**: 10-day Moving Average of the Close price
   - **MA50**: 50-day Moving Average of the Close price

---

## 💡 Strategy Logic

- **Buy (Shares = 1)** when MA10 > MA50
- **Do Nothing (Shares = 0)** otherwise

### Code Snippet:

```python
fb1['Shares'] = [1 if fb1.loc[ei, 'MA10'] > fb1.loc[ei, 'MA50'] else 0 for ei in fb1.index]
fb1['Close1'] = fb1['Close'].shift(-1)
fb1['Profit'] = [fb1.loc[ei, 'Close1'] - fb1.loc[ei, 'Close'] if fb1.loc[ei, 'Shares'] == 1 else 0 for ei in fb1.index]

📈 Visualization & Results
Profit/Loss Plot:
fb1['Profit'].plot()
plt.axhline(y=0, color='red')

Cumulative Wealth:
fb1['wealth'] = fb1['Profit'].cumsum()
fb1['wealth'].plot()
plt.title('Total money you win is {}'.format(fb1.loc[fb1.index[-2], 'wealth']))


📦 Requirements
Install dependencies using:
pip install pandas matplotlib

---

## ✅ Bonus: `requirements.txt`

If you're using a Python script or notebook, create a `requirements.txt` file with the libraries:
pandas
matplotlib

To install everything later:
```bash
pip install -r requirements.txt
```

📉 Conclusion
The results show that this simple moving average crossover strategy did not result in profitable returns over the selected period for Facebook stock.

🤝 Acknowledgement
Special thanks to AI guidance for helping bypass data download limits and suggesting alternative methods to fetch stock data.
