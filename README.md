# Currency Pair Reversal Trading Strategy

## Overview

This repository contains the implementation and backtesting results of a sophisticated currency pair reversal trading strategy that capitalizes on mean reversion opportunities in the foreign exchange market. The strategy exploits temporary divergences between correlated currency pairs to generate consistent profits.

## Strategy Description

### Core Concept
Our trading strategy is based on the principle that closely correlated currency pairs tend to revert to their historical relationship after temporary divergences. When two correlated pairs move in opposite directions on a given day, it often presents an arbitrage-like opportunity.

### Entry Criteria
The strategy enters trades when the daily percentage change of two correlated currency pairs closes in **opposite directions**:
- **Sell** the pair with positive percentage change
- **Buy** the pair with negative percentage change

### Exit Criteria
Positions are held until the combined portfolio achieves an overall profit of **+0.5%**, ensuring consistent and manageable profit targets.

## Currency Pair Combinations

### 1. AUDUSD vs EURUSD Strategy
- **Timeframe:** Daily (GMT+0, No DST adjustment)
- **Position Sizing:** 
  - EURUSD: 1.3 standard lots
  - AUDUSD: 1.0 standard lot
- **Correlation Logic:** Both pairs are USD-denominated majors with significant correlation

### 2. GBPUSD vs EURUSD Strategy  
- **Timeframe:** Daily (GMT+0, No DST adjustment)
- **Position Sizing:**
  - EURUSD: 1.3 standard lots
  - GBPUSD: 1.0 standard lot
- **Correlation Logic:** EUR and GBP often move together against USD due to geographical proximity

### 3. AUDUSD vs AUDCAD Strategy
- **Timeframe:** Daily (GMT+0)
- **Position Sizing:**
  - AUDCAD: 1.5 standard lots
  - AUDUSD: 1.0 standard lot
- **Correlation Logic:** Both pairs share AUD as base currency, creating natural correlation

## Risk Management

### Spread Costs
- **EURUSD:** 1.0 pip spread
- **GBPUSD:** 1.2 pip spread  
- **AUDUSD:** 1.2 pip spread
- **AUDCAD:** 2.0 pip spread

### Swap Costs (per standard lot per night)
- **EURUSD:** Long -6.60 USD, Short +1.90 USD
- **GBPUSD:** Long -2.49 USD, Short -4.79 USD
- **AUDUSD:** Long -3.80 USD, Short -3.03 USD
- **AUDCAD:** Long -6.60 USD, Short -9.00 USD

### Position Sizing Logic
Position sizes are carefully calibrated based on:
1. Historical volatility of each pair
2. Correlation strength
3. Risk parity principles
4. Account size optimization

## Strategy Performance Summary

| Strategy | Win Rate | Total Trades | Average Profit | Total Return | Sharpe Ratio |
|----------|----------|--------------|----------------|--------------|--------------|
| AUDUSD/EURUSD | 97.60% | 458 | 0.6339% | 290.34% | 0.4605 |
| GBPUSD/EURUSD | 96.09% | 409 | 0.5590% | 228.63% | 0.5157 |
| AUDUSD/AUDCAD | 95.99% | 349 | 0.5206% | 181.69% | 0.4546 |

## Key Advantages

1. **High Win Rate:** Consistently achieving 95%+ win rates across all strategies
2. **Consistent Profits:** Fixed profit target ensures regular income
3. **Market Neutral:** Strategy profits from relative movements, not directional bets
4. **Risk Controlled:** Limited downside with predetermined exit criteria
5. **Scalable:** Can be applied to multiple correlated pairs simultaneously

## Implementation Details

### Data Requirements
- Daily OHLC data for all currency pairs
- Real-time spread and swap cost data
- Economic calendar for major announcements

### Execution Timing
- Signals generated at daily close (GMT+0)
- Trades executed at next day's market open
- Positions monitored continuously until profit target reached

### Technology Stack
- **Python 3.x** for strategy implementation
- **Pandas** for data manipulation and analysis
- **NumPy** for mathematical calculations
- **Matplotlib/Seaborn** for visualization
- **Jupyter Notebooks** for backtesting and analysis

## Files Structure

```
├── AUDUSD_EURUSD.ipynb          # AUDUSD/EURUSD strategy implementation
├── GBPUSD_EURUSD.ipynb          # GBPUSD/EURUSD strategy implementation  
├── AUDUSD_AUDCAD.ipynb          # AUDUSD/AUDCAD strategy implementation
├── trade_report_*.csv           # Individual strategy trade reports
├── *_1day_D1.csv               # Historical price data
└── README.md                    # This file
```

## Risk Warnings

- Past performance does not guarantee future results
- Currency trading involves substantial risk of loss
- Strategy effectiveness may change during extreme market conditions
- Proper position sizing and risk management are essential
- Consider transaction costs and slippage in live trading

## Getting Started

1. Install required Python packages:
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

2. Load historical data for your chosen currency pairs

3. Run the appropriate Jupyter notebook for backtesting

4. Analyze results and adjust parameters as needed

5. Implement paper trading before live deployment

## Contact

For questions about strategy implementation or performance analysis, please refer to the detailed notebooks and trade reports included in this repository.