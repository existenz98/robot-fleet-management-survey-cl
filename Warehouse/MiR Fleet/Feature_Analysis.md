# MiR Fleet (Mobile Industrial Robots) — Feature Analysis

**Product:** MiR Fleet — centralized fleet management for MiR AMRs (+ VDA5050 adapter, Meili FMS partnership)
**Domain:** Warehouse & intralogistics (own hardware; VDA5050 interop)
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** · **[L] Likely** · **[I] Inferred**.

---

## Research & Summary

MiR Fleet (Mobile Industrial Robots, part of Teradyne) is centralized fleet-management software that controls a fleet of **MiR AMRs** from a single station across a facility, of any size. Core capabilities are the logistics staples: **task allocation** (automated and non-automated assignments), **traffic control** (predict/regulate bottlenecks), **route planning/optimization**, and **intelligent charging schedules** to maximize availability. It exposes an **open REST API** for third-party integration and adds **VDA5050** interoperability via an open adapter "starter kit" that bridges its REST API to the MQTT messages the standard requires — and MiR also partners with **Meili FMS** to unify mixed-brand fleets. It's own-hardware-first but increasingly interoperable. Evidence is Confirmed at the capability level (product page + VDA5050 articles); detailed operator-config (recurrence, zone editors) is in the Enterprise documentation, not fully captured here. Intralogistics orientation.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Operations team"]

  subgraph UI["MiR FLEET — centralized console"]
    UIM["Mission planning · monitoring · traffic · charging"]
  end

  subgraph CORE["MiR FLEET SOFTWARE"]
    direction LR
    TASK["Task<br/>allocation"]
    TRAF["Traffic<br/>control"]
    ROUTE["Route<br/>planning"]
    CHG["Charging<br/>management"]
    TASK ~~~ TRAF ~~~ ROUTE ~~~ CHG
  end

  subgraph EXT["INTEGRATION"]
    direction LR
    API["Open REST API"]
    VDA["VDA5050 adapter<br/>(REST to MQTT)"]
    IO["Elevators / doors / PLC / WMS"]
  end

  subgraph FLEET["MiR AMRs (own; + VDA5050 third-party)"]
    ROB["MiR AMR fleet"]
  end

  OP --> UI
  UI --> CORE
  CORE <-->|"integration"| EXT
  CORE <-->|"missions · traffic · charging"| ROB

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style EXT fill:#ECFCCB,stroke:#65A30D,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((MiR Fleet))
    Robot and Hardware Support
      Own MiR AMRs
      VDA5050 adapter
      Meili FMS partnership
    Task Allocation
      Automated assignments
      Non-automated assignments
    Traffic Control
      Bottleneck prediction
      Route planning
    Charging
      Intelligent schedules
    Integration
      Open REST API
      Elevators doors PLC
      WMS ERP
    Multi-floor
      Cross-level operation
    User Interface
      Centralized console
    Deployment
      Fleet server
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("MiR Fleet"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["Own MiR AMRs"]
  G1 --> G1b["VDA5050 adapter (REST to MQTT)"]
  G1 --> G1c["Meili FMS partnership (mixed brand)"]

  R --> G2["2 · Task Allocation"]
  G2 --> G2a["Automated assignments"]
  G2 --> G2b["Non-automated assignments"]

  R --> G3["3 · Traffic Control"]
  G3 --> G3a["Bottleneck prediction/regulation"]
  G3 --> G3b["Route planning / optimization"]

  R --> G4["4 · Charging"]
  G4 --> G4a["Intelligent charging schedules"]

  R --> G5["5 · Integration"]
  G5 --> G5a["Open REST API"]
  G5 --> G5b["Elevators / doors / PLC"]
  G5 --> G5c["WMS / ERP"]

  R --> G6["6 · Multi-floor"]
  G6 --> G6a["Cross-level operation"]

  R --> G7["7 · User Interface"]
  G7 --> G7a["Centralized console"]

  R --> G8["8 · Deployment"]
  G8 --> G8a["Fleet server"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Own MiR AMRs** — fleets of any size [C]
- **1.2 VDA5050 adapter** — open "starter-kit" bridging REST API ↔ MQTT [C]
- **1.3 Meili FMS partnership** — unify mixed-brand fleets [C]

### 2. Task Allocation
- **2.1 Automated assignments** [C]
- **2.2 Non-automated assignments** [C]
- **2.3 Dispatch most-suitable robot** [L]

### 3. Traffic Control & Routing
- **3.1 Bottleneck prediction & regulation** [C]
- **3.2 Route planning / optimization** [C]

### 4. Charging
- **4.1 Intelligent charging schedules** — maximize availability, reduce downtime [C]

### 5. Integration
- **5.1 Open REST API** for third-party integration [C]
- **5.2 Elevators / doors / PLC** [L]
- **5.3 WMS / ERP** [L]

### 6. Multi-floor
- **6.1 Cross-level operation** [L]

### 7. User Interface & UX
- **7.1 Centralized console** (MiR Fleet / MiR Fleet Enterprise) [C]
- **7.2 Map-based view** [L]

### 8. Deployment & Architecture
- **8.1 Fleet server** (dedicated host) [L]
- **8.2 Cloud option** — not confirmed [I]

### 9. Connectivity & Protocols
- **9.1 REST API** [C]
- **9.2 VDA5050 (via adapter, MQTT)** [C]
- **9.3 OPC-UA / others** — not confirmed [I]

#### UI Screenshots

**Mir fleet choose robot**
![Mir fleet choose robot](Images/ui_mir-fleet-choose-robot.png)

**Mir insights screens**
![Mir insights screens](Images/ui_mir-insights-screens.png)

**Mir insights**
![Mir insights](Images/ui_mir-insights.png)

**Robot software driving**
![Robot software driving](Images/ui_robot-software-driving.png)

**Robot software relocating**
![Robot software relocating](Images/ui_robot-software-relocating.png)

---

> **Gaps / to verify:** scheduling recurrence, zone/map editor specifics, cloud vs on-prem, RBAC/SSO, and exact WMS/elevator integrations. Confirm via MiR Fleet Enterprise documentation or a demo. Logistics-only orientation.

## Sources
- mobile-industrial-robots.com (MiR Fleet, VDA5050 articles), MiR Fleet Enterprise Documentation (PDF)
