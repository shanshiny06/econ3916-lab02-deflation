# econ3916-lab02-deflation
# Deflating Economic Data — Nominal vs. Real

## Objective

This project demonstrates how to separate genuine purchasing-power gains from inflation-driven price increases, using FRED economic data and a reusable deflation framework applied independently to wages and the Big Mac Index.

## Methodology

- Pulled CPI and average hourly earnings data directly from the FRED API, requiring no API key for the core data retrieval
- Built a reusable `deflate_series()` function implementing the standard deflation formula (Nominal / CPI × Base-Year CPI) to convert any nominal time series into constant-dollar terms
- Converted average hourly earnings into constant 2020 dollars, isolating the real change in purchasing power from the nominal change in wages
- Applied the same deflation methodology to the U.S. Big Mac price, using `.asof()` to align the semi-annual Big Mac observations with the nearest prior monthly CPI reading before deflating
- Compared nominal price growth, real (inflation-adjusted) price growth, and CPI growth over the identical date range for the Big Mac series
- Built an interactive deflation explorer with a base-year slider, confirming that shifting the base year changes the dollar level of a real series but never its underlying growth rate

## Key Findings

- Nominal average hourly earnings rose from $2.50 to $32.53 over the sample period, while real earnings — expressed in constant 2020 dollars — moved from $20.92 to $25.20, showing that a substantial share of the apparent wage growth reflects inflation rather than a genuine gain in purchasing power
- The U.S. Big Mac price rose 178% in nominal terms over the same window, but only 43% once adjusted for inflation, with CPI itself rising 95% over the identical period — demonstrating that headline nominal price changes can overstate the real cost increase of even a simple, single product by a wide margin
- Across both series, the gap between nominal and real growth is fully accounted for by cumulative inflation, reinforcing that nominal figures alone are an unreliable guide to changes in real economic value
- The interactive explorer confirms a core property of deflation: re-expressing a real series in a different base year rescales its dollar level but leaves its real growth rate unchanged, regardless of which year is chosen as the reference point
