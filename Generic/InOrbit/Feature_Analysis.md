# InOrbit — Feature Analysis

**Product:** InOrbit Space Intelligence (enterprise) + InOrbit Ground Control (robot developers)
**Domain:** Generic / vendor-agnostic robot orchestration (RobOps)
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** = stated in official or vendor materials · **[L] Likely** = vendor marketing or strongly implied · **[I] Inferred** = deduced / not stated.

---

## Research & Summary

InOrbit is a vendor-agnostic robot orchestration platform branding itself as a "central nervous system" / "Physical AI" layer for enterprise robot operations — coordinating robots, people, fixed IoT infrastructure (cameras, doors) and enterprise systems (WMS/ERP/WES/MES) from one place. Its enterprise product, **Space Intelligence**, is presented as a set of named pillars (Unified Command, Interoperability, Multi-Vehicle Orchestration, Intelligent Orchestration, AI-driven Insights, AI-Powered Optimization), while **InOrbit Ground Control** serves robot developers with monitoring/teleoperation/data tooling. Architecturally it is a cloud platform that connects to robots via an edge agent / InOrbit Connect, aggregates telemetry, and exposes dashboards + APIs; it integrates NVIDIA Isaac Sim for simulation and RTLS for tracking non-robotic assets and staff. Stated environments are warehouses and manufacturing, so security/patrol-specific detection is not emphasized. Evidence is strong for the existence of the feature pillars (all on official pages) but thinner at the deepest configuration level, because InOrbit's public site describes capabilities more than detailed settings — those leaves are tagged Likely/Inferred. No clean public console screenshots were availablees; the UI section uses illustrative site imagery and flags where true captures are needed.

**UI quality impression (subjective):** marketing imagery suggests a modern, map-and-dashboard web console with heavy data-viz and an AI "copilot" chat; needs a live demo (inorbit.ai/in-action) to assess properly.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Enterprise users · operators · developers"]

  subgraph UI["WEB CONSOLE — dashboards, maps, RobOps Copilot"]
    UIM["Monitoring · Missions · Analytics · Alerts"]
  end

  subgraph CORE["INORBIT SPACE INTELLIGENCE — cloud platform"]
    direction LR
    UC["Unified<br/>Command"]
    ORCH["Intelligent &<br/>Multi-Vehicle<br/>Orchestration"]
    AI["AI Vision &<br/>Insights"]
    OPT["AI-Powered<br/>Optimization"]
    UC ~~~ ORCH ~~~ AI ~~~ OPT
  end

  subgraph EXT["ENTERPRISE & INFRASTRUCTURE"]
    direction LR
    BIZ["WMS / ERP / WES / MES"]
    IOT["IoT / fixed infra<br/>cameras, doors"]
    RTLS["RTLS<br/>assets + staff"]
  end

  subgraph FLEET["HETEROGENEOUS ROBOT FLEET"]
    AGENT["Edge agent / InOrbit Connect"]
    ROB["AMRs · dogs · drones · humanoids<br/>(multi-vendor)"]
    AGENT --> ROB
  end

  SIM["NVIDIA Isaac Sim<br/>simulation"]

  OP --> UI
  UI --> CORE
  CORE <-->|"integrations / APIs"| EXT
  CORE <-->|"telemetry · commands · teleop"| AGENT
  CORE <-->|"sim"| SIM

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style EXT fill:#ECFCCB,stroke:#65A30D,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((InOrbit))
    Robot and Hardware Support
      Heterogeneous types
      Vendor agnosticism
      Robot Directory
      Edge agent Connect
    Connectivity and Integration
      Enterprise systems
      IoT and fixed infra
      RTLS
      APIs
    Fleet Monitoring and Ops
      Real-time dashboards
      Alerts and incidents
      Teleoperation
    Orchestration
      Unified Command
      Intelligent Orchestration
      Multi-Vehicle Orchestration
      Missions
    AI and Analytics
      AI vision
      AI event summaries
      RobOps Copilot
      AI optimization
    Simulation
      NVIDIA Isaac Sim
    User Interface and UX
      Web console
      Dashboards and maps
    Deployment and Scale
      Cloud
      Multi-site
    Security and Governance
      Access control
    Editions
      Enterprise
      Ground Control
      Edu
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("InOrbit"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["Heterogeneous robot types"]
  G1 --> G1b["Vendor agnosticism"]
  G1 --> G1c["Robot Directory"]
  G1 --> G1d["Edge agent / InOrbit Connect"]

  R --> G2["2 · Connectivity and Integration"]
  G2 --> G2a["Enterprise systems"]
  G2 --> G2b["IoT and fixed infrastructure"]
  G2 --> G2c["RTLS"]
  G2 --> G2d["APIs / webhooks"]

  R --> G3["3 · Fleet Monitoring and Ops"]
  G3 --> G3a["Real-time dashboards"]
  G3 --> G3b["Alerts and incidents"]
  G3 --> G3c["Teleoperation"]

  R --> G4["4 · Orchestration"]
  G4 --> G4a["Unified Command"]
  G4 --> G4b["Intelligent Orchestration"]
  G4 --> G4c["Multi-Vehicle Orchestration"]
  G4 --> G4d["Missions"]

  R --> G5["5 · AI and Analytics"]
  G5 --> G5a["AI vision"]
  G5 --> G5b["AI event summaries"]
  G5 --> G5c["RobOps Copilot"]
  G5 --> G5d["AI optimization"]

  R --> G6["6 · Simulation"]
  G6 --> G6a["NVIDIA Isaac Sim"]

  R --> G7["7 · User Interface and UX"]
  G7 --> G7a["Web console"]
  G7 --> G7b["Dashboards and maps"]

  R --> G8["8 · Deployment and Scale"]
  G8 --> G8a["Cloud"]
  G8 --> G8b["Multi-site"]

  R --> G9["9 · Security and Governance"]
  G9 --> G9a["Access control"]

  R --> G10["10 · Editions"]
  G10 --> G10a["Enterprise"]
  G10 --> G10b["Ground Control"]
  G10 --> G10c["Edu"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Heterogeneous robot types** — manage mixed form factors [C]
  - 1.1.1 AMRs / mobile robots [C]
  - 1.1.2 Other form factors (drones, quadrupeds, humanoids) [L]
- **1.2 Vendor / brand agnosticism** — multiple vendors on one screen [C]
- **1.3 Robot Directory** — catalogue of supported/integrated robots [C]
- **1.4 Onboarding via on-robot InOrbit agent / InOrbit Connect** [C]
  - 1.4.1 On-robot **InOrbit agent** bridges robot ↔ cloud [C]
  - 1.4.2 **ROS1 and ROS2 pub/sub** integration [C]
  - 1.4.3 **Language bindings / SDK** for custom software on the robot [C]
  - 1.4.4 Connector framework for new models [L]

### 2. Connectivity & Integration
- **2.1 Enterprise systems** — WMS / ERP / WES / MES [C]
- **2.2 Fixed infrastructure / IoT** — cameras, doors, IoT devices [C]
- **2.3 RTLS** — real-time location systems for assets + staff [C]
- **2.4 Developer APIs** [C]
  - 2.4.1 Public APIs + docs/tutorials [C]
  - 2.4.2 Webhooks / event access [I]

### 3. Fleet Monitoring & Operations
- **3.1 Real-time monitoring** [C]
  - 3.1.1 **Fleet status matrix** — per-robot grid across attributes (Battery, ROS state, WiFi, Mode, Ping time, Localization) [C]
  - 3.1.2 Per-robot dashboards (e.g. vitals, navigation) [C]
  - 3.1.3 Live data / video views (Ground Control) [C]
  - 3.1.4 Add **simulated robots** alongside real ones [C]
- **3.2 Alerting & incident management** [C]
  - 3.2.1 **Incident list** — severity levels, open/resolved status, robot, **component**, time [C]
  - 3.2.2 Audit logs / fleet logs [C]
  - 3.2.3 AI event summaries to cut log review [C]
  - 3.2.4 Configurable alert rules [I]
- **3.3 Teleoperation & remote intervention** (Ground Control) [C]
  - 3.3.1 Map-based navigation + teleop dashboard [C]
  - 3.3.2 Tablet/iPad remote operation [C]
- **3.4 Time Capsule** — capture/replay robot state around an incident for root-cause analysis [C]

### 4. Orchestration & Workflow
- **4.1 Unified Command** — business execution system bridging orders↔robots [C]
- **4.2 Intelligent Orchestration** — map/manage/orchestrate workflows; human+robot collaboration [C]
- **4.3 Multi-Vehicle Orchestration** — coordinate robots, people, non-robotic assets via RTLS [C]
- **4.4 Missions** — define/dispatch/execute missions [C]
  - 4.4.1 **Mission KPI dashboards** (grouped by site) — success rate, mission frequency (per day/robot), avg duration, avg incidents/mission, with trend sparklines + time-range selector [C]
  - 4.4.2 Scheduling / recurring missions [I]
- **4.5 Application modules (console tabs)** — Executive, Fleet, Robot, Navigation, Missions, Time Capsule, **Depalletizing**, **Orchestration** [C]

### 5. AI & Analytics
- **5.1 AI-powered vision** — proactive incident identification [C]
- **5.2 AI-Powered Optimization** [C]
  - 5.2.1 Bottleneck identification [C]
  - 5.2.2 Resource-allocation optimization [C]
  - 5.2.3 Continuous learning / adaptive optimization [C]
- **5.3 RobOps Copilot** — AI ops assistant, in-console chat [C]
  - 5.3.1 Natural-language retrieval (e.g. "show me the Time Capsules of the stopped-robot incident") [C]
  - 5.3.2 Slack integration (Copilot in Slack) [C]
  - 5.3.3 Mission-review assistance [C]

### 6. Simulation
- **6.1 InOrbit simulations** — NVIDIA Isaac Sim integration [C]

### 7. User Interface & UX
- **7.1 Web console (tabbed)** — Executive · Fleet · Robot · Navigation · Missions · Time Capsule · Depalletizing · Orchestration [C]
- **7.2 Fleet status matrix + per-robot dashboards** [C]
- **7.3 Map-based navigation / teleop views** [C]
- **7.4 Tablet / iPad remote operation** [C]
- **7.5 3D / game-engine UI** — not evident [I]

### 8. Deployment & Scale
- **8.1 Cloud platform** [C]
- **8.2 Multi-site operations** — aggregate across sites [L]
- **8.3 Edge component** (agent on robot/site) [L]
- **8.4 On-prem option** — not confirmed [I]

### 9. Security & Governance
- **9.1 User access management** [I]
- **9.2 SSO / enterprise security** [I]

### 10. Editions / Packaging
- **10.1 Enterprise (Space Intelligence)** [C]
- **10.2 Ground Control (robot developers)** [C]
- **10.3 Edu Edition** [C]

#### UI Screenshots

**Fleet view — status matrix + incident list**
![InOrbit fleet view](Images/ui_control-fleet-view.png)

**Missions — per-site KPI dashboards** (success rate, frequency, duration, incidents)
![InOrbit missions view](Images/ui_control-missions-view.png)

**KPI dashboard**
![InOrbit KPI dashboard](Images/ui_kpi-dashboard.png)

**Map navigation + teleoperation**
![InOrbit navigation teleop](Images/ui_navigation-teleop-dashboard.png)

**Per-robot dashboard**
![InOrbit robot dashboard](Images/ui_robot-status-dashboard.png)

**RobOps Copilot — in-console chat (Time Capsule retrieval)**
![InOrbit RobOps Copilot](Images/feature_copilot-in-control.png)

**Architecture — on-robot agent + ROS1/ROS2 + SDK**
![InOrbit on-robot architecture](Images/arch_robot-sdk-diagram.png)

---

> **Gaps / to verify:** deep config (recurrence rules, zone editors, charging), on-prem availability, SSO/security certs, mobile app, and true console UI — confirm via inorbit.ai/docs, developer.inorbit.ai, or a demo. Security/patrol detection is not a stated focus (warehouse/manufacturing orientation).

## Sources
- inorbit.ai (home), inorbit.ai/spaceintelligence; directory.inorbit.ai, connect.inorbit.ai, developer.inorbit.ai (referenced)
