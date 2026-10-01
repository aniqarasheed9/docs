# 📊 LBT — Live Pay Benchmarking

[← Back to overview](../README.md)

## What it's for

This app answers the question **"are we paying competitively?"** — it compares a
company's pay against market data and/or its own payroll, and shows where it sits
(e.g. "we're paying this role at the 40th percentile of the market").

## What's inside

```mermaid
flowchart TB
    subgraph LBT["📊 LBT App"]
        REPORTLIST[Report list<br/>processing / ready / error]
        WIZARD[5-step report wizard]
        BYTITLE[Instant view<br/>by job title — no wizard]
    end

    WIZARD --> STEP1[1. Region & data source]
    STEP1 --> STEP2[2. Peer companies<br/>sector/industry or custom basket]
    STEP2 --> STEP3[3. Which pay element<br/>base, bonus, total, etc.]
    STEP3 --> STEP4[4. Percentiles to show<br/>10th/25th/50th/75th/90th]
    STEP4 --> STEP5[5. Data recency settings]
    STEP5 --> GENERATE[Generate report<br/>runs in the background]
    GENERATE --> REPORTLIST
```

## The three data sources you can compare against

```mermaid
flowchart LR
    A["Tom Data<br/>(offers built in TOM)"] --> RESULT[Benchmarking result]
    B["Payroll Data<br/>(uploaded actual payroll)"] --> RESULT
    C["Aggregate<br/>(both combined)"] --> RESULT
```

## In plain words

- **"Tom Data"** = offers that were modelled in the TOM app (what the company
  *intended* to pay).
- **"Payroll Data"** = actual payroll numbers the company uploaded (what people are
  *actually* being paid).
- **"Aggregate"** = both pooled together into one combined picture.
- A report can take a little while to build (it's crunching a lot of numbers), so it
  shows as **"Processing"** and the screen automatically checks back every few
  seconds until it's ready to download.
- There's also a **quick, instant view** ("By Title") for when you just want a fast
  answer for one job title, without going through the full wizard.
- To protect competitor privacy, a **custom peer group** (comparing against specific
  chosen companies) requires at least 10 companies in the group — so no single
  competitor's pay can be reverse-engineered from the result.
