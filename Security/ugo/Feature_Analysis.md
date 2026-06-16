# ugo — Feature Analysis

**Product:** ugo robots (Pro / Mini / Ex) + ugo Platform (integrated robot management)
**Domain:** Security & patrol + inspection (own hardware, but platform manages 3rd-party robots & CCTV)
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** = stated in official or vendor materials · **[L] Likely** = vendor marketing or strongly implied · **[I] Inferred** = deduced / not stated.

---

## Research & Summary

ugo (Japan) builds avatar/DX robots (ugo Pro, ugo Mini, ugo Ex) that act as security + inspection assistants, plus the **ugo Platform** — a cloud application for integrated robot management. A distinctive trait is that the platform manages **ugo robots AND other robots, including CCTVs**, giving it partial vendor-agnostic reach, and the robots are a **hybrid of teleoperation and autonomy** (human-like, with robot hands that can operate lifts and trigger auto-sensor doors). For security it patrols, detects strangers/violence/smoke/fire, streams live footage to a monitoring room, and supports live two-way calls; for inspection it reads analog/digital meters (AI-converted to data), captures thermal/environmental readings, and auto-compiles checkpoint reports. The platform offers map creation + route generation, automated robot "flows," a pose editor, scheduling, and no-code usability. Evidence is Confirmed at the capability level (distributor product page + notes) but deep configuration (recurrence rules, protocol list) is not enumerated. Combines patrol + inspection + CCTV under one console — a strong security-plus-facilities fit.

**UI quality impression (subjective):** the ugo Platform shows dedicated screens for robot management/remote control, automated flow setup, map creation, and a pose editor — operationally complete; real screenshots exist on the distributor page.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Guards / monitoring room"]

  subgraph UI["ugo PLATFORM — cloud app (no-code)"]
    UIM["Robot mgmt · remote control · route creation · pose editor · reports"]
  end

  subgraph CORE["ugo CLOUD — management & AI"]
    direction LR
    PAT["Patrol &<br/>flow automation"]
    DET["AI detection<br/>& alerts"]
    INSP["Inspection &<br/>meter reading"]
    REP["Reporting"]
    PAT ~~~ DET ~~~ INSP ~~~ REP
  end

  subgraph EXT["FACILITY SYSTEMS"]
    direction LR
    CCTV["CCTV cameras"]
    LIFT["Elevators / auto doors"]
  end

  subgraph FLEET["ROBOTS (ugo + others)"]
    ROB["ugo Pro / Mini / Ex<br/>+ other robots"]
  end

  OP --> UI
  UI --> CORE
  CORE <-->|"manage / stream"| CCTV
  CORE <-->|"robot hands + integration"| LIFT
  CORE <-->|"control · telemetry · teleop"| ROB

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style EXT fill:#ECFCCB,stroke:#65A30D,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((ugo Platform))
    Robot and Hardware Support
      ugo Pro Mini Ex
      Manages other robots
      Manages CCTVs
      Robot hands
    Connectivity and Integration
      Elevator integration
      Auto-sensor doors
      CCTV integration
    Patrol and Mission
      Map creation
      Route generation
      Automated robot flow
      Pose editor
    Teleoperation and Remote
      Remote control
      Live calls
      Avatar teleop
    Detection and AI
      Stranger detection
      Violence smoke fire
      Live footage alerts
    Inspection and Data
      Meter reading
      Thermal and environment
      Checkpoint data
    Reporting
      Auto report to management
    User Interface
      Cloud app no-code
    Safety
      Collision sensors
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("ugo Platform"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["ugo Pro / Mini / Ex"]
  G1 --> G1b["Manages other robots"]
  G1 --> G1c["Manages CCTVs"]
  G1 --> G1d["Robot hands (operate lifts)"]

  R --> G2["2 · Connectivity and Integration"]
  G2 --> G2a["Elevator integration"]
  G2 --> G2b["Auto-sensor doors"]
  G2 --> G2c["CCTV integration"]

  R --> G3["3 · Patrol and Mission"]
  G3 --> G3a["Map creation"]
  G3 --> G3b["Route generation"]
  G3 --> G3c["Automated robot flow"]
  G3 --> G3d["Pose editor"]

  R --> G4["4 · Teleoperation and Remote"]
  G4 --> G4a["Remote control"]
  G4 --> G4b["Live calls / interaction"]
  G4 --> G4c["Avatar teleop"]

  R --> G5["5 · Detection and AI"]
  G5 --> G5a["Stranger detection"]
  G5 --> G5b["Violence / smoke / fire"]
  G5 --> G5c["Live footage + alerts"]

  R --> G6["6 · Inspection and Data"]
  G6 --> G6a["Meter reading (AI)"]
  G6 --> G6b["Thermal / environmental"]
  G6 --> G6c["Checkpoint data"]

  R --> G7["7 · Reporting"]
  G7 --> G7a["Auto report to management"]

  R --> G8["8 · User Interface"]
  G8 --> G8a["Cloud app (no-code)"]

  R --> G9["9 · Safety"]
  G9 --> G9a["Collision detection sensors"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Own robot models** — ugo Pro (full), ugo Mini (compact), ugo Ex [C]
- **1.2 Manages third-party robots** [C]
- **1.3 Manages CCTVs** [C]
- **1.4 Robot hands / manipulation** — operate lifts, wave at auto-sensor doors [C]
- **1.5 LiDAR mapping** [C]

### 2. Connectivity & Integration
- **2.1 Elevator / lift integration** (physical + system) [C]
- **2.2 Auto-sensor door operation** [C]
- **2.3 CCTV integration** [C]
- **2.4 Protocol list** — not stated [I]

### 3. Patrol & Mission
- **3.1 Map creation** — LiDAR-based building mapping [C]
- **3.2 Route generation** — create pre-set patrol routes [C]
- **3.3 Automated robot flow** — set up automated sequences [C]
- **3.4 Pose editor** [C]
- **3.5 Scheduling** [L]
  - 3.5.1 Recurrence rules [I]

### 4. Teleoperation & Remote
- **4.1 Remote management & control** [C]
- **4.2 Live communication (calls)** [C]
- **4.3 Avatar teleop + autonomy hybrid** [C]
- **4.4 Multi-screen remote monitoring** [C]

### 5. Detection & AI
- **5.1 Threat detection** [C]
  - 5.1.1 Strangers / intruders [C]
  - 5.1.2 Violent behavior [C]
  - 5.1.3 Smoke / fire [C]
- **5.2 Live footage to monitoring room + alerts** [C]
- **5.3 Image/video capture for records** [C]

### 6. Inspection & Data
- **6.1 Meter reading** — analog/digital → digital data via AI [C]
- **6.2 Thermal camera data capture** [C]
- **6.3 Environmental sensor data** [C]
- **6.4 Checkpoint data along route** [C]

### 7. Reporting
- **7.1 Automatic report compilation** — sent to management [C]

### 8. User Interface & UX
- **8.1 Cloud-based app** [C]
- **8.2 No-code / intuitive (no programming)** [C]
- **8.3 Modules** — robot mgmt, remote control, flow automation, map creation, pose editor, reports [C]

### 9. Safety
- **9.1 Collision detection sensors** [C]

### 10. Deployment & Commercial
- **10.1 Cloud-based platform** [C]
- **10.2 Hybrid robot + human operations; scalable** [C]
- **10.3 Cost reduction >50%** claim [C]

#### UI Screenshots
![ugo robot management](https://static.wixstatic.com/media/a8d377_279bf067971e468aa66b358b34a790fb~mv2.png/v1/fill/w_295,h_186,al_c,q_85,enc_avif,quality_auto/ugo-robot-management.png)
![ugo automated flow](https://static.wixstatic.com/media/a8d377_abf59601f1604ee69aa9d9fbff46a3e3~mv2.png/v1/fill/w_295,h_186,al_c,q_85,enc_avif,quality_auto/ugo-robot-flow-automation.png)
![ugo map creation](https://static.wixstatic.com/media/a8d377_975d237f8a23463c8ae2842c67dd4825~mv2.png/v1/crop/x_3,y_0,w_1097,h_550/fill/w_295,h_137,al_c,q_85,enc_avif,quality_auto/ugo-robot-map-creation.png)

**Pose editor**
![ugo pose editor](https://static.wixstatic.com/media/a8d377_79adcfcf8eb147ac9e919bd0f6bdf711~mv2.png/v1/fill/w_295,h_200,al_c,q_85,enc_avif,quality_auto/a8d377_79adcfcf8eb147ac9e919bd0f6bdf711~mv2.png)

**Create patrol route**
![ugo create route](https://static.wixstatic.com/media/a8d377_1893ebf30258419da36a19fae6bc31c6~mv2.jpg/v1/crop/x_0,y_11,w_684,h_434/fill/w_471,h_299,al_c,q_80,enc_avif,quality_auto/ugo-robot-create-route.jpg)

---

> **Gaps / to verify:** protocol/integration list (ROS/VDA5050/REST/API), exact scheduling/recurrence options, which third-party robots are supported, on-prem vs cloud, security/RBAC, pricing. Confirm via ugo.plus or a vendor demo.

## Sources
- ourglass.com.sg/ugo-robot (distributor), ugo.plus
