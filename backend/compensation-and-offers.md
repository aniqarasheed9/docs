# 💰 Backend: Compensation Data & Offers

[← Back to overview](../README.md)

## What this group does

This is the heart of the product. It stores every piece of pay-related reference
data a company keeps, and uses that data to build and calculate job offers.

## What's inside

```mermaid
flowchart TB
    subgraph CompData["Compensation Reference Data"]
        GRADES2[Grades]
        SALARY3[Salary ranges]
        CASH2[Cash allowances]
        STI2[Short-term bonus plans]
        LTI2[Long-term incentive plans]
        BENEFITS2[Benefit plans]
        PAYROLL3[Internal payroll]
        MARKETDATA[Market pay data]
    end

    subgraph OfferEngine["Offer Modelling"]
        BUILD[Build an offer]
        CALC["Calculation engine<br/>(works out the full pay package)"]
        VERSION[Version history<br/>for revised offers]
    end

    CUSTOMJOBS[Custom Job Titles<br/>company-specific job names]

    CompData -->|feeds| CALC
    BUILD --> CALC
    CALC --> VERSION
    CUSTOMJOBS -.labels roles for.-> BUILD
```

## How an offer's pay is calculated

```mermaid
flowchart TB
    START[An offer is being built<br/>for a specific role + grade] --> BASE["A. Base salary<br/>from the salary range for that grade"]
    BASE --> BONUS["B. Short-term bonus<br/>a % of base salary"]
    BONUS --> LTI3["C. Long-term incentive<br/>equity / stock award"]
    LTI3 --> SIGNON["D. Sign-on bonus<br/>one-time joining payment"]
    SIGNON --> BENEFITS3["E. Benefits<br/>health cover, etc."]
    BENEFITS3 --> TOTAL["F. Totals<br/>added together into one package"]
    TOTAL --> COMPARE["Compared to the role's current pay<br/>→ shows % increase/decrease"]
```

## Module-by-module

### Compensation Reference Data
The "master list" of everything a company has set up: grade pay bands, allowance
rules, bonus plan rules, incentive plan rules, benefit rules, and the payroll +
market data it has uploaded. This data **changes in versions** — every time it's
updated, a new version is saved rather than overwriting the old one, so nothing is
silently lost.

### Offer Modelling
Takes the reference data above and uses it to build an actual offer for a real
candidate. A person picks a role/grade, and the system suggests numbers, which can
then be adjusted by hand before the offer is finalized and sent.

### Custom Job Titles
Some companies use their own internal job titles that don't match a standard
catalog. This module lets a company define its own list, which then gets mapped to
the standard list behind the scenes (see the AI mapping feature in
[Benchmarking & Data Import](benchmarking-and-import.md)).
