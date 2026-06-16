# Rapyuta Robotics — Feature Analysis

**Product:** rapyuta.io (cloud-robotics DevOps + multi-robot platform); robot solutions (ASRS, PA-AMR, AFL) built on it
**Domain:** Generic / cloud-robotics platform with multi-robot coordination
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** = stated in official or vendor materials · **[L] Likely** = vendor marketing or strongly implied · **[I] Inferred** = deduced / not stated.

---

## Research & Summary

Rapyuta Robotics positions **rapyuta.io** as "the world's first all-in-one DevOps platform for cloud-connected robots," covering the lifecycle from CI/CD and deployment of robotics applications to remote fleet management — with a command-line interface and a browser-based **AMR Dashboard** for site configuration, fleet monitoring, and intervention/control. Its technical philosophy is explicitly **heterogeneous multi-robot coordination**: build simpler robots that each do a subset of tasks and coordinate them, underpinned by patented multi-robot planning/control and the open-source **ALICA** coordination framework. The full-stack software spans single-robot localization & motion planning up to multi-robot task assignment and route planning, plus award-winning spatial-AI **perception** and **large-scale simulation** on Unreal Engine (rclUE). Commercially, Rapyuta is also a warehouse-robot solution vendor (pick-assist AMR, ASRS, automated forklift) — those are logistics solutions built on the platform; the FMS-relevant layer is rapyuta.io itself. Evidence is Confirmed for the platform pillars (home + technology pages) but the deepest operational settings (mission scheduling specifics, traffic rules) aren't enumerated publicly and are tagged Likely/Inferred. Orientation is developer/DevOps + warehouse, not security/inspection.

**UI quality impression (subjective):** developer-leaning — a CLI plus a browser AMR Dashboard; likely more engineer-oriented than the turnkey security consoles. Needs a live look to judge.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Developers · operators"]

  subgraph UI["INTERFACES — CLI + browser AMR Dashboard"]
    UIM["Site config · fleet monitor · intervene/control"]
  end

  subgraph CORE["rapyuta.io — CLOUD-NATIVE ROBOTICS PLATFORM"]
    direction LR
    DEV["DevOps:<br/>CI/CD · deploy"]
    STACK["Full stack:<br/>localization ·<br/>motion planning"]
    COORD["Multi-robot:<br/>task assign ·<br/>routing (ALICA)"]
    PERC["Perception<br/>(spatial AI)"]
    SIM["Simulation<br/>(Unreal/rclUE)"]
    DEV ~~~ STACK ~~~ COORD ~~~ PERC ~~~ SIM
  end

  subgraph FLEET["CLOUD-CONNECTED ROBOT FLEET (heterogeneous)"]
    ROB["PA-AMR · ASRS · automated forklift<br/>+ other cloud-connected robots"]
  end

  OP --> UI
  UI --> CORE
  CORE <-->|"deploy · monitor · control"| FLEET

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((rapyuta.io))
    Robot and Hardware Support
      Heterogeneous robots
      Hardware-agnostic stack
      Own AMR ASRS AFL
    DevOps Platform
      CI CD
      Deployment
      CLI tooling
      Remote management
    Multi-robot Coordination
      ALICA framework
      Task assignment
      Route planning
      Motion planning
    Perception
      Spatial AI vision
    Fleet Monitoring and Control
      AMR Dashboard
      Intervene and control
    Simulation
      Unreal Engine rclUE
    User Interface
      CLI
      Browser dashboard
    Deployment and Architecture
      Cloud-native
      Edge robots
    Open Source
      ALICA
      rclUE
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("rapyuta.io"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["Heterogeneous robots"]
  G1 --> G1b["Hardware-agnostic full stack"]
  G1 --> G1c["Own AMR / ASRS / AFL"]

  R --> G2["2 · DevOps Platform"]
  G2 --> G2a["CI/CD"]
  G2 --> G2b["Deployment"]
  G2 --> G2c["CLI tooling"]
  G2 --> G2d["Remote fleet management"]

  R --> G3["3 · Multi-robot Coordination"]
  G3 --> G3a["ALICA framework"]
  G3 --> G3b["Task assignment"]
  G3 --> G3c["Route planning"]
  G3 --> G3d["Motion planning & control"]

  R --> G4["4 · Perception"]
  G4 --> G4a["Spatial AI vision"]

  R --> G5["5 · Fleet Monitoring and Control"]
  G5 --> G5a["AMR Dashboard"]
  G5 --> G5b["Intervene and control"]

  R --> G6["6 · Simulation"]
  G6 --> G6a["Unreal Engine (rclUE)"]

  R --> G7["7 · User Interface"]
  G7 --> G7a["CLI"]
  G7 --> G7b["Browser dashboard"]

  R --> G8["8 · Deployment and Architecture"]
  G8 --> G8a["Cloud-native"]
  G8 --> G8b["Edge robots"]

  R --> G9["9 · Open Source"]
  G9 --> G9a["ALICA"]
  G9 --> G9b["rclUE"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Heterogeneous robot coordination** — many simple robots coordinated vs one complex robot [C]
- **1.2 Hardware-agnostic full-stack software** [C]
- **1.3 Own robot solutions on the platform** — PA-AMR (pick-assist), ASRS, AFL (automated forklift) [C]

### 2. DevOps Platform (rapyuta.io)
- **2.1 Continuous integration / deployment** of robotics apps to fleet or cloud [C]
- **2.2 Remote management of physical robot fleet** [C]
- **2.3 Command-line tooling** — build/deploy + observe distributed resources from terminal [C]
- **2.4 Cloud-native architecture** for distributed, constantly-updated software stacks [C]

### 3. Multi-Robot Coordination & Planning
- **3.1 Distributed intelligence** — patented multi-robot planning/control [C]
  - 3.1.1 ALICA open-source coordination/control framework [C]
- **3.2 Task assignment** for multi-robot systems [C]
- **3.3 Route planning** for multi-robot systems [C]
- **3.4 Motion planning & control** (single-robot agility, dynamic obstacles) [C]

### 4. Perception
- **4.1 Spatial-AI vision** — object identification + pose estimation [C]

### 5. Fleet Monitoring & Control
- **5.1 AMR Dashboard** — browser-based [C]
  - 5.1.1 Configure site [C]
  - 5.1.2 Monitor AMR fleet [C]
  - 5.1.3 Intervene / control robots [C]
  - 5.1.4 **Overview dashboard** — order progress (new / in-progress / complete / failed / cancelled / exception), robot-status breakdown (offline / standby / charging / start-prep / picking), **per-batch completion %**, order priority; EN/JA UI [C]
  - 5.1.5 **Change order/robot priority** on the fly [C]
- **5.2 Data Monitoring** — real-time picking productivity & robot-ops data [C]
- **5.3 User App (on tablet PC)** — simple UI, associates work hands-free [C]
- **5.4 Warehouse Management App** — operation status/results reporting (**coming soon**) [C]

### 6. Simulation
- **6.1 Large-scale simulation** — evaluate robot mix, predict ROI before deployment [C]
  - 6.1.1 Built on Unreal Engine (rclUE, open source) [C]

### 7. User Interface & UX
- **7.1 CLI** [C]
- **7.2 Browser AMR Dashboard** [C]
- **7.3 3D / game-engine operator UI** — simulation uses UE; operator UI specifics not detailed [I]

### 8. Deployment & Architecture
- **8.1 Cloud-native platform** [C]
- **8.2 Edge / on-robot software stack** [C]
- **8.3 On-prem option** — not stated [I]

### 9. Open Source
- **9.1 ALICA** — multi-robot coordination framework [C]
- **9.2 rclUE** — ROS + Unreal Engine integration [C]

### 10. Connectivity & Protocols
- **10.1 ROS-based stack** (ALICA/rclUE are ROS-oriented) [L]
- **10.2 WMS integration** — rapyuta.io edge talks to various WMS via **API or FTP** [C]
- **10.3 VDA5050 / MQTT** — not explicitly stated [I]

#### UI Screenshots

**PA-AMR Overview dashboard** (orders, robot status, per-batch %)
![Rapyuta PA-AMR dashboard](Images/ui_pa-amr-dashboard.png)

**Changing order/robot priority**
![Rapyuta changing priority](Images/ui_pa-amr-changing-priority.png)

**rapyuta.io platform overview**
![rapyuta.io overview](Images/ui_rapyuta-io-overview.png)

**AFL remote monitor**
![Rapyuta AFL remote monitor](Images/ui_afl-remote-monitor.jpg)

**Architecture — PA-AMR system design (User App · edge · cloud · WMS · monitoring)**
![Rapyuta PA-AMR system design](Images/arch_pa-amr-system-design.png)

**Architecture — distributed intelligence (ALICA)**
![Rapyuta distributed intelligence](Images/arch_distributed-intelligence.jpg)

---

> **Gaps / to verify:** protocol support (ROS version, VDA5050, MQTT, REST), mission scheduling/traffic-control specifics, security/tenancy model, on-prem availability, and pricing. Note: Rapyuta is both a platform and a warehouse-solution vendor — clarify which layer applies to a given engagement. Confirm via rapyuta.io docs or a demo.

## Sources
- rapyuta-robotics.com/rapyuta-io, /technology
