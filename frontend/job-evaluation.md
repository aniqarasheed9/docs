# 📋 JE — Job Evaluation

[← Back to overview](../README.md)

## What it's for

Before you can pay someone fairly, you need to know **how big the job is**. JE is a
questionnaire-driven tool: you answer a set of standard questions about a role
(how much decision-making it involves, how much it affects financial results, etc.),
and the system works out which **grade** that role belongs to.

## What's inside

```mermaid
flowchart TB
    subgraph JE["📋 JE App"]
        DASH3[Dashboard]
        LIST[Job evaluation list]
        CREATE[Create a new evaluation]
        QUESTIONNAIRE[Answer the questionnaire<br/>5 scored categories]
        RESULT[System calculates<br/>a grade]
        GRADEDEF[Grade definitions<br/>what each grade means]
        LIBRARY[Job library<br/>reusable job descriptions]
    end

    LIST --> CREATE --> QUESTIONNAIRE --> RESULT
    RESULT -->|uses| GRADEDEF
    LIBRARY -.reference.-> CREATE
```

## The five scoring categories

```mermaid
flowchart LR
    A[Knowledge & Skills] --> SCORE[Total score]
    B[Problem Solving] --> SCORE
    C[Stakeholder Management] --> SCORE
    D[Decision Impact] --> SCORE
    E[Financial / Non-financial<br/>Responsibility] --> SCORE
    SCORE --> GRADE[Matched to a Grade<br/>e.g. Grade 5]
```

## In plain words

- Think of it like a **points-based test for a job**, not for a person. The same
  questionnaire, answered the same way, always gives the same grade — it's
  consistent across the whole company.
- Each category contributes points; the points are added up and matched against the
  company's grade bands (set up by an admin) to land on a final grade.
- Once a role has a grade, **TOM** uses that grade to pull the right salary range,
  bonus target, and benefits when building an offer for that role — JE and TOM are
  connected through the grade, even though they're separate apps.
- An evaluation moves through a simple lifecycle: **Open → Evaluated → Submitted/Closed.**
