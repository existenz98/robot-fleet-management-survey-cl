# Ascento — Feature Analysis

**Product:** Ascento Guard (outdoor security robot) + Ascento management app, delivered as RaaS
**Domain:** Security & patrol (own hardware; outdoor)
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** · **[L] Likely** · **[I] Inferred**.

---

## Research & Summary

Ascento (Switzerland) provides an autonomous, all-terrain **outdoor security guard robot** ("Ascento Guard") plus a management/monitoring **app**, sold as a turnkey **Robotics-as-a-Service**. The robot carries thermal/RGB/infrared cameras, runs ~8h on battery with autonomous charging, is all-weather, and performs the classic outdoor-guarding detections: people on premises, perimeter integrity, thermal anomalies, parking/ALPR, doors & windows, and property lights (10,000+ AI detections/day quoted). The FMS-relevant layer is the app: control anytime/anywhere, encrypted live communication, **configurable patrol scheduling**, AI-powered reports, and **integration with existing video management systems (VMS)**. Service is turnkey (install in hours, training, 24/7 support, 95% uptime guarantee). Evidence is Confirmed at the capability level from the website; deep config (recurrence options, API, multi-vendor) isn't published. Single-robot-type vendor (own hardware) — not a multi-vendor orchestration layer, but a close fit to the outdoor-guarding use case.

**UI quality impression (subjective):** clean mobile/app-style control surface ("control your robot anytime, anywhere") with AI reports and VMS hand-off; consumer-grade polish.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Security team / operators"]

  subgraph UI["ASCENTO APP — control, schedule, reports"]
    UIM["Live control · patrol scheduling · AI reports"]
  end

  subgraph CORE["ASCENTO CLOUD (RaaS)"]
    direction LR
    CTRL["Remote control<br/>encrypted comms"]
    SCH["Patrol<br/>scheduling"]
    AID["AI detection<br/>& reports"]
    CTRL ~~~ SCH ~~~ AID
  end

  VMS["Existing VMS<br/>(video mgmt system)"]

  subgraph FLEET["ASCENTO GUARD (own hardware)"]
    ROB["All-terrain outdoor robot<br/>thermal · RGB · IR cameras"]
  end

  OP --> UI
  UI --> CORE
  CORE <-->|"video integration"| VMS
  CORE <-->|"control · telemetry · video"| ROB

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((Ascento))
    Robot and Hardware Support
      Own Ascento Guard
      Thermal RGB IR cameras
      8h battery auto-charge
      All-weather
    Detection
      People on premises
      Perimeter integrity
      Thermal anomaly
      Parking ALPR
    Management App
      Remote control
      Encrypted comms
      Patrol scheduling
      AI reports
    Integration
      VMS integration
    Service
      Turnkey RaaS
      24/7 support
      Uptime guarantee
    User Interface
      App control surface
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("Ascento"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["Own Ascento Guard"]
  G1 --> G1b["Thermal / RGB / IR cameras"]
  G1 --> G1c["8h battery, auto-charge"]
  G1 --> G1d["All-weather"]

  R --> G2["2 · Detection"]
  G2 --> G2a["People on premises"]
  G2 --> G2b["Perimeter integrity"]
  G2 --> G2c["Thermal anomaly"]
  G2 --> G2d["Parking / ALPR"]

  R --> G3["3 · Management App"]
  G3 --> G3a["Remote control"]
  G3 --> G3b["Encrypted live comms"]
  G3 --> G3c["Configurable patrol scheduling"]
  G3 --> G3d["AI-powered reports"]

  R --> G4["4 · Integration"]
  G4 --> G4a["VMS integration"]

  R --> G5["5 · Service"]
  G5 --> G5a["Turnkey RaaS"]
  G5 --> G5b["24/7 support"]
  G5 --> G5c["Uptime guarantee (95%)"]

  R --> G6["6 · User Interface"]
  G6 --> G6a["App control surface"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Own Ascento Guard** — autonomous all-terrain outdoor robot [C]
- **1.2 Payload** — thermal, RGB, infrared cameras [C]
- **1.3 Endurance** — 8h+ battery, autonomous charging [C]
- **1.4 All-weather** — rain/snow/wind, safe autonomous speed [C]
- **1.5 Vendor-agnostic?** — No; single own robot [I]

### 2. Detection
- **2.1 Detect people on premises** [C]
- **2.2 Verify perimeter integrity** [C]
- **2.3 Thermal anomaly scanning** [C]
- **2.4 Parking control / ALPR** [C]
- **2.5 Check doors & windows; record property lights** [C]
- **2.6 ~10,000 AI detections/day** (scale) [C]

### 3. Management App (FMS layer)
- **3.1 Remote control** — anytime, anywhere [C]
- **3.2 Encrypted live communication** [C]
- **3.3 Configurable patrol scheduling** [C]
  - 3.3.1 Recurrence/calendar options [I]
- **3.4 AI-powered reports** [C]

### 4. Integration
- **4.1 VMS integration** — works with existing video management systems [C]
- **4.2 API / other integrations** — not stated [I]

### 5. Service & Commercial
- **5.1 Turnkey RaaS** — hired by the hour [C]
- **5.2 Install in hours** [C]
- **5.3 Training & onboarding** [C]
- **5.4 24/7 support; 95% uptime guarantee; fast replacements** [C]

### 6. User Interface & UX
- **6.1 App control surface** — "control your robot anytime, anywhere" [C]
- **6.2 3D/map operator view** — not detailed [I]

### 7. Deployment & Architecture
- **7.1 Cloud app + robot** [C]
- **7.2 On-prem option** — not stated [I]

#### UI Screenshots

**Control your robot**
![Control your robot](Images/ui_control-your-robot.png)

**Web interface analytics**
![Web interface analytics](Images/ui_web-interface-analytics.png)

---

> **Gaps / to verify:** API/integration breadth beyond VMS, scheduling recurrence detail, multi-robot fleet scaling, RBAC/SSO, on-prem, pricing specifics. Confirm via ascento.ai/resources or a demo. Outdoor single-robot focus; not a multi-vendor orchestration platform.

## Sources
- ascento.ai (home, resources)
