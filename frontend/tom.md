# 💰 TOM — Pay Data & Offers

[← Back to overview](../README.md)

## What it's for

TOM is the biggest and busiest app. It's where a company:
- keeps its **pay data** (salary ranges, bonus rules, benefits, grades) up to date, and
- builds **job offers** for candidates, with the system calculating the full pay
  package automatically.

## What's inside

```mermaid
flowchart TB
    subgraph TOM["💰 TOM App"]
        direction TB
        DASH2[Dashboard<br/>summary charts]

        subgraph PayData["Pay data setup"]
            GRADES[Grade setup]
            SALARY[Salary ranges]
            CASH[Cash allowances]
            STI[Short-term bonus plans]
            LTI[Long-term incentive plans]
            BENEFITS[Benefit plans]
            PAYROLL[Internal payroll data]
            MARKET[Market pay data]
        end

        subgraph Offers["Offers"]
            OFFERLIST[Offer list<br/>active / past / drafts]
            BUILDER[Offer builder<br/>3-step wizard]
            EMAIL[Offer email / PDF]
            AIBOT[🤖 AI suggestions<br/>while building an offer]
        end

        PROFILE[Company profile & structure]
        SUBADMINS[Manage company users]
    end

    DASH2 --> PayData
    DASH2 --> Offers
    PayData -->|feeds data into| BUILDER
    BUILDER --> AIBOT
    BUILDER --> EMAIL
    BUILDER --> OFFERLIST
```

## Building an offer, step by step

```mermaid
flowchart LR
    A[1. Position details<br/>role, grade, location] --> B[2. Candidate details<br/>name, current pay]
    B --> C[3. Offer modeller<br/>system auto-fills pay from<br/>the company's pay data]
    C --> D{Looks good?}
    D -->|Yes| E[Save as Placed]
    D -->|Needs changes| C
    E --> F[Send offer email / PDF]
    E --> G[Later: Accept / Reject / Revise]
```

## In plain words

- **Pay data setup** is the "ingredients" — grades, salary bands, bonus rules, etc.
  Someone (usually an admin) keeps these current, often by uploading a spreadsheet
  (CSV) instead of typing each row by hand.
- **The offer builder** is the "recipe" — it takes those ingredients and, once you
  pick a role and grade, automatically works out a suggested pay package. A person can
  then adjust it before sending.
- **The AI assistant** watches the offer as it's being built and surfaces things like
  "this offer is below the usual range for this grade" — a second pair of eyes, not a
  replacement for a human decision.
- **Offers can be revised** — if terms change after an offer is placed, a new version
  is created rather than overwriting history, so there's always a record of what was
  originally offered.
