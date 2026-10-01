# 🤖 Backend: AI & Dashboards

[← Back to overview](../README.md)

## What this group does

These modules add a layer of **interpretation** on top of the raw data — either
through AI-generated commentary, or through aggregated charts.

## What's inside

```mermaid
flowchart TB
    subgraph AI2["AI Insights (two engines)"]
        INSIGHTS["AI Insights<br/>short pay-trend messages"]
        MODULE["AI Offer Analysis<br/>alerts on a specific offer"]
    end

    subgraph DASH3["Dashboard Aggregation"]
        AGG["Combines offers + payroll<br/>+ evaluations into one view"]
    end

    OFFER2[An offer is being built] --> INSIGHTS
    OFFER2 --> MODULE
    AllData[Offers, payroll, grades] --> AGG
```

## What the two AI engines each do

```mermaid
flowchart LR
    subgraph Insights["AI Insights"]
        I1[Pay trend commentary]
        I2[Retention risk note]
        I3[Roles in demand]
    end

    subgraph Analysis["AI Offer Analysis"]
        A1[Compa-ratio review]
        A2[Conversion-rate likelihood]
        A3[Critical pay positioning]
        A4[Payment recommendation]
    end

    Offer3[Offer being viewed] --> Insights
    Offer3 --> Analysis
```

## Module-by-module

### AI Insights
Generates short, plain-language notes while someone is looking at an offer — things
like "pay for this role has been trending up," or "this role carries elevated
retention risk." If the AI service is unavailable, the system falls back to
pre-written generic messages so the feature never breaks completely.

### AI Offer Analysis
A more structured alert system: it runs a set of rule-based checks on an offer
(e.g. is the compa-ratio too low? how competitive is this against critical pay
benchmarks?) and then uses AI to turn the result into a readable summary with a
recommendation.

> **Note:** both of these are AI "copilots," not AI decision-makers — every suggestion
> is shown to a human, who makes the final call on the offer.

### Dashboard Aggregation
Pulls together data that lives in several other modules (offers, payroll, salary
ranges, evaluated grades) and pre-calculates the numbers the Dashboard app's charts
need — like compa-ratio and pay-gap figures — so the front-end can render them
quickly without doing heavy math itself.
