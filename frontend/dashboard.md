# 📈 Dashboard — Analytics

[← Back to overview](../README.md)

## What it's for

This app turns all the data sitting in the other apps into **charts and trends** —
a bird's-eye view for leadership and HR to spot patterns (e.g. "are we underpaying
women relative to men in this grade?", "how has our hiring pay trended this year?").

## What's inside

```mermaid
flowchart TB
    subgraph Dashboard["📈 Dashboard App"]
        FILTERS[Cascading filters<br/>company → region → grade → function]
        CHARTS[Charts<br/>compa-ratio, pay gap, hiring trends]
        BENCH2[Also includes the<br/>benchmarking screens]
    end

    FILTERS --> CHARTS
```

## Where the numbers come from

```mermaid
flowchart LR
    OFFERS[Offers<br/>from TOM] --> DASHSVC[Dashboard calculations]
    PAYROLL2[Payroll data<br/>from TOM] --> DASHSVC
    SALARY2[Salary ranges<br/>from TOM] --> DASHSVC
    JE2[Evaluated grades<br/>from JE] --> DASHSVC
    DASHSVC --> CHARTS2[Charts on screen]
```

## In plain words

- The Dashboard app **doesn't collect any new data itself** — it reads data that was
  already entered in TOM and JE, and presents it visually.
- **Compa-ratio** is one of the headline numbers: it tells you, on average, whether
  people are being paid above, at, or below the middle of their pay range.
- Filters let you slice the picture down — e.g. "just this region" or "just this
  grade" — without needing to ask IT for a custom report.
