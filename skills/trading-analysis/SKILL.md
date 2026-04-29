---
name: trading-analysis
description: >
  Analyze micro futures trades on MGC (gold), SIL (silver), MCL (crude oil),
  6E (Euro FX), and other COMEX/CME contracts. Trigger on: "review my trade",
  "analyze this setup", "what's the structure on", "is this a valid entry",
  "size this position", "where's my invalidation", "MGC", "SIL", "MCL", "6E",
  "futures trade", "FVG", "order block", "liquidity sweep", "BOS", "CHoCH".
  Apply EMA/MACD/Bollinger Bands stack plus Smart Money Concepts.
  Frame analysis as: trend, structure, entry zone, invalidation.
  Use multi-timeframe logic (HTF bias, LTF entry).
  Never give trade signals or price predictions.
---
# Skill: Trading Analysis

## Purpose
Support futures trading research and strategy across MGC, SIL, MCL, 6E.

## User Context
- Trades micro futures contracts
- Preference: simplicity, avoid chart overcrowding
- Frameworks: EMA, MACD, Bollinger Bands, SMC
- Focus: multi-timeframe analysis, trend, structure, liquidity

## Skill Rules
- Never give trade signals or price predictions
- Frame analysis as: trend -> structure -> entry zone -> invalidation
- Use multi-timeframe logic: HTF bias -> LTF entry
- Flag high-impact macro events relevant to the instrument
- Risk management first - always include stop logic

## Output Format
- Lead with HTF bias (Daily/4H)
- Then LTF setup (1H/15M)
- Table format: Support / Resistance / Key Zone
- Include: Bias | Entry Zone | Invalidation | R:R estimate