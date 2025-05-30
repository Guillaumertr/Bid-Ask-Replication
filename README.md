# 📈 Bid-Ask Replication with Transaction Costs

This notebook focuses on replicating a **European call option** in a market with **proportional transaction costs**, i.e., where a spread exists between the bid and ask prices. In this context, the classical Black-Scholes Delta hedging must be adapted.

---

## 🔍 Objective

The goal is to analyze and implement two pricing and hedging methods in the presence of transaction costs:

- **Standard Delta Hedging** with direct transaction costs.
- **Leland's approach**, which modifies the volatility to account for these costs analytically.

---

## 🛠️ Methodology

### 1. Delta Hedging with Bid-Ask Spread
- At each rebalancing date, a hedge is placed based on the current delta.
- The **transaction cost is explicitly computed** for each rebalance as:
  
$$\text{Cost} = \text{bid-ask spread} \times | \Delta_t - \Delta_{t-1} | \times S_t$$

- This approach reflects the real trading cost incurred when adjusting the hedge.

### 2. ⚡ Leland Volatility Adjustment
Instead of modeling transaction costs directly, we **adjust the volatility** used in the Black-Scholes model. This is based on the approach proposed by **Leland (1985)**.

The **effective volatility** becomes:
$$\sigma_L = \sigma \left(1 + \sqrt{\frac{2}{\pi}} \frac{c}{\sigma} \sqrt{\Delta t} \right)$$

Where:
- $\sigma$ is the original volatility.
- $c$ is the proportional cost per unit traded.
- $\Delta t$ is the hedging interval.

This modified volatility inflates the option price to **preemptively compensate for expected costs**, and allows hedging as if the market were frictionless again — with an appropriately inflated volatility.

---

## 📊 Outputs

- Replication profit and loss with and without transaction costs.
- Comparison between:
  - Naive delta hedging with bid-ask spread.
  - Leland-adjusted pricing and hedging.

- Histograms of the hedging errors for both approaches.

---

## ✅ Key Takeaways

- In the presence of bid-ask spreads, classical delta-hedging results in **systematic losses** if not adjusted.
- Leland’s approach provides a **robust approximation** and is computationally efficient.
- The performance of both methods can depend on the **hedging frequency** and the **spread size**.

---

## 🧠 References

- Leland, H. E. (1985). "Option pricing and replication with transactions costs." *The Journal of Finance*.

## 👤 Author

👨‍💻 Guillaume Routier  
🎓 MSc Probabilité & Finance – École Polytechnique & Sorbonne Université  
📬 [Contact me on LinkedIn](https://www.linkedin.com/in/guillaume-routier/)

---

## 📌 Disclaimer

These notebooks are for educational and demonstrative purposes only. They do not constitute financial advice.
