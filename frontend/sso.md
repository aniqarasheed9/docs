# 🔑 SSO — Login & Company Setup

[← Back to overview](../README.md)

## What it's for

This is the **front door** to the whole product. It's the only app where people
actually type a password. Once logged in here, the system remembers who you are
everywhere else — you never log in again for the other four apps.

It's also where a company gets **set up** for the first time, and where new users
get invited.

## What's inside

```mermaid
flowchart TB
    subgraph SSO["🔑 SSO App"]
        LOGIN[Login screen<br/>email + password]
        FORGOT[Forgot / reset password]
        PICKER[App picker<br/>choose which tool to open]
        COMPANYLIST[Company list<br/>switch between companies]
        COMPANYSETUP[Create / edit a company]
        USERS[Manage company users<br/>invite, roles, permissions]
    end

    LOGIN --> PICKER
    PICKER --> COMPANYLIST
    COMPANYLIST --> COMPANYSETUP
    COMPANYLIST --> USERS
    PICKER -->|opens| OTHERAPPS[The other 4 apps]
```

## How login works for everyone else

```mermaid
sequenceDiagram
    participant P as 👤 Person
    participant SSO as 🔑 SSO app
    participant Shared as 🍪 Shared login (cookie)
    participant Other as 💰/📋/📊/📈 Any other app

    P->>SSO: Logs in with email + password
    SSO->>Shared: Saves "you are logged in" for all apps
    P->>SSO: Picks an app, e.g. TOM
    SSO->>Other: Opens that app
    Other->>Shared: Checks "is this person logged in?"
    Shared-->>Other: Yes — here's who they are and what they can do
    Other-->>P: Shows the app, already logged in
```

## In plain words

- **Nobody else has a real login screen.** The other four apps just check "did this
  person already log in through SSO?" — if yes, they're let straight in.
- **Company admins** use this app to invite teammates and decide what each teammate
  is allowed to see or edit (their "role").
- **A person can belong to more than one company** — the company picker is how they
  switch between them.
