FX Time-Series Momentum Strategy
A systematic momentum strategy across a basket of seven G10 currency pairs,
built as a research backtest rather than a demo.
What it does
Each trading day, for every currency pair, the strategy:

Measures the trailing 3-month return — the momentum signal.
Goes long pairs in an uptrend and short pairs in a downtrend.
Scales each position by recent realised volatility, so every pair
contributes comparable risk to the portfolio.
Charges a transaction cost on every change in position.

Why it is built this way

Real data. Daily prices are pulled from Yahoo Finance — there are no
simulated random walks anywhere in the pipeline.
No look-ahead. Signals are lagged one day before being traded: the
return earned on day t uses the position decided with data up to t-1.
Costs included. Performance is reported both gross and net of a
configurable basis-point transaction cost.
Robustness checks. Results are split into in-sample and out-of-sample
periods, and a lookback parameter sweep shows the result does not depend on
curve-fitting one window.
Honest metrics. Sharpe, Sortino, maximum drawdown, Calmar, hit rate and
turnover are reported exactly as they come out of the data.

Running it
bashpip install yfinance pandas numpy matplotlib
python fx_momentum_strategy.py
The script prints the performance tables and saves an equity-curve chart to
fx_momentum_results.png.
Results
Run the script and paste the output tables here, alongside
fx_momentum_results.png.
Limitations and extensions

Uses daily close prices; intraday execution and slippage are not modelled.
Transaction costs are a single flat estimate, not pair-specific bid-ask
spreads.
Carry (interest-rate differentials) is not included. The natural next step
is a combined carry + momentum strategy, since the two factors tend to
perform in different market regimes.
