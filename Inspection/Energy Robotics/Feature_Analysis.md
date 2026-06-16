# Energy Robotics (now Korial) — Feature Analysis

**Product:** Korial enterprise AI platform (Kore · Connect · Recreate · Sustain) — formerly Energy Robotics
**Domain:** Inspection & field robotics — **hardware-agnostic** autonomous-operations platform
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** · **[L] Likely** · **[I] Inferred**.

---

## Research & Summary

Korial (the 2026 rebrand of Energy Robotics) is a **hardware-agnostic enterprise AI platform** that unifies robots, drones, cameras, and sensors into one operating layer for autonomous industrial inspection and operations — turning telemetry into verified insight and orchestrated action. Unlike the OEM-bound inspection tools, Korial explicitly manages **mixed fleets** (e.g., Boston Dynamics Spot + ANYmal + drones, as at Shell Rheinland). Its architecture has four named components: **Kore** (the AI core — LLM, agentic workflows, embedded skills, device/site supervision, robot control), **Connect** (integration backbone for APIs and IT/OT data exchange), **Recreate** (digital twins, spatial site views, virtual mission testing/simulation), and **Sustain** (onboarding & support). Proven at scale (1M+ inspections, 100+ global deployments; Shell, Evonik, E.ON, BP, Chevron, Merck) and ISO 27001 certified. This is one of the strongest **vendor-agnostic inspection** platforms in the survey. Evidence is Confirmed at the platform-architecture level; deep operator-config detail is thinner.

**UI quality impression (subjective):** the platform dashboard shows mission stats, robot status, inspection coverage, site insights, and an AI chat box — a modern, AI-forward ops console. A real dashboard image is on the platform page.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Operators · solution architects · executives"]

  subgraph UI["KORIAL CONSOLE — dashboard + AI chat"]
    UIM["Mission stats · robot status · inspection coverage · site insights"]
  end

  subgraph CORE["KORIAL PLATFORM (cloud, hardware-agnostic)"]
    direction LR
    KORE["Kore<br/>AI core / control"]
    CONN["Connect<br/>APIs · IT/OT"]
    RECR["Recreate<br/>digital twin / sim"]
    SUST["Sustain<br/>support"]
    KORE ~~~ CONN ~~~ RECR ~~~ SUST
  end

  subgraph EXT["ENTERPRISE IT/OT"]
    BIZ["External systems · reporting · governance"]
  end

  subgraph FLEET["MIXED FLEET (any hardware)"]
    ROB["Ground robots (Spot, ANYmal) · drones · fixed cameras · sensors"]
  end

  OP --> UI
  UI --> CORE
  CORE <-->|"APIs · data exchange"| EXT
  CORE <-->|"control · telemetry · missions"| ROB

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style EXT fill:#ECFCCB,stroke:#65A30D,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((Korial))
    Robot and Hardware Support
      Hardware-agnostic
      Robots drones cameras sensors
      Mixed fleet
    Kore AI Core
      LLM and agentic workflows
      Embedded skills
      Robot control
      Device site supervision
    Connect Integration
      APIs
      IT OT exchange
    Recreate
      Digital twin
      Spatial site views
      Virtual mission testing
    Autonomous Operations
      Autonomous missions
      Remotely supervised
      Risk-aware inspection
    Data and Analytics
      Inspection data processing
      Verified insight
      Dashboards
    Security
      ISO 27001
    Sustain
      Onboarding and support
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("Korial"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["Hardware-agnostic"]
  G1 --> G1b["Robots / drones / cameras / sensors"]
  G1 --> G1c["Mixed fleet"]

  R --> G2["2 · Kore (AI core)"]
  G2 --> G2a["LLM + agentic workflows"]
  G2 --> G2b["Embedded skills"]
  G2 --> G2c["Robot control"]
  G2 --> G2d["Device/site supervision"]

  R --> G3["3 · Connect (integration)"]
  G3 --> G3a["APIs"]
  G3 --> G3b["IT/OT data exchange"]

  R --> G4["4 · Recreate"]
  G4 --> G4a["Digital twin"]
  G4 --> G4b["Spatial site views"]
  G4 --> G4c["Virtual mission testing"]

  R --> G5["5 · Autonomous Operations"]
  G5 --> G5a["Autonomous missions"]
  G5 --> G5b["Remotely supervised"]
  G5 --> G5c["Risk-aware inspection"]

  R --> G6["6 · Data and Analytics"]
  G6 --> G6a["Inspection data processing"]
  G6 --> G6b["Verified insight"]
  G6 --> G6c["Dashboards"]

  R --> G7["7 · Security"]
  G7 --> G7a["ISO 27001"]

  R --> G8["8 · Sustain"]
  G8 --> G8a["Onboarding & support"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Hardware-agnostic** — any asset, any device [C]
  - 1.1.1 Ground robots (Spot, ANYmal), drones, fixed cameras, sensors [C]
  - 1.1.2 Mixed/heterogeneous fleet coordination (e.g., robots + drone at Shell) [C]

### 2. Kore (AI core)
- **2.1 LLM + agentic workflows** [C]
- **2.2 Embedded skills** [C]
- **2.3 Robot control** [C]
- **2.4 Device & site supervision** [C]
- **2.5 Self-reinforcing intelligence** (live telemetry → action) [C]

### 3. Connect (integration backbone)
- **3.1 APIs** [C]
- **3.2 IT/OT data exchange** — stream inspection data/telemetry/insight to external systems [C]

### 4. Recreate (modeling & simulation)
- **4.1 Digital twins** [C]
- **4.2 Spatial site views** [C]
- **4.3 Virtual mission testing** before live deployment [C]

### 5. Autonomous Operations
- **5.1 Autonomous missions** [C]
- **5.2 Remotely-supervised missions** [C]
- **5.3 Risk-aware inspection / routine rounds** [C]

### 6. Data & Analytics
- **6.1 Inspection data collection, processing, analytics** [C]
- **6.2 Verified insight / orchestrated action** [C]
- **6.3 Dashboards** — mission stats, robot status, inspection coverage, site insights [C]

### 7. Security & Compliance
- **7.1 ISO 27001 certified** [C]

### 8. Sustain (service)
- **8.1 Structured onboarding, industrial-grade support, success partnership** [C]

### 9. Deployment & Architecture
- **9.1 Enterprise cloud AI platform** [C]
- **9.2 On-prem / edge split** — not fully specified [I]

### 10. User Interface & UX
- **10.1 Web dashboard + AI chat box** [C]
- **10.2 3D / spatial site views** (via Recreate) [C]

#### UI Screenshots

**Kore — operations dashboard** (mission stats, robot status, inspection coverage, AI chat)
![Korial Kore dashboard](https://cdn.prod.website-files.com/69cba68755c8be38e980bc5c/69f8b093a08045266c746779_Frame%204%20(1).avif)

**Connect — mission report + inspection data + facility schematic**
![Korial Connect view](https://cdn.prod.website-files.com/69cba68755c8be38e980bc5c/69f838918a9556d1bf7c78e0_Korial-Platform-Recreate-Module-Placeholder.webp)

**Recreate — immersive 3D / digital-twin feature view**
![Korial Recreate immersive view](https://cdn.prod.website-files.com/69cba68755c8be38e980bc5c/69f837c01497eb9da81d3f3e_Korial-Immersive-View-Placeholder.webp)

---

> **Gaps / to verify:** protocol list (ROS/VDA5050/MQTT), on-prem availability, RBAC/SSO specifics, exact supported-robot list, and pricing. Strong vendor-agnostic inspection peer — closest in spirit to a "generic" platform but inspection-focused. Confirm via korial.com/enterprise-ai-platform or a demo.

## Sources
- korial.com (home, enterprise-ai-platform, customer stories)
