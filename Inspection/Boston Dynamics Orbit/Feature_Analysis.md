# Boston Dynamics — Orbit — Feature Analysis

**Product:** Orbit™ — orchestration & intelligence software for Boston Dynamics robots (Spot, Stretch, eventually Atlas)
**Domain:** Inspection & field robotics (own hardware)
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** · **[L] Likely** · **[I] Inferred**.

---

## Research & Summary

Orbit is Boston Dynamics' fleet-orchestration and facility-intelligence software for its **own** robots (Spot, Stretch, and eventually Atlas) — not vendor-agnostic. It combines classic FMS (mission editing/scheduling, map-based dashboard, remote operation, performance summaries, multi-site fleet health) with deep **inspection intelligence** (visual/acoustic/thermal data, automated in-product + email anomaly alerts, remote inspection authoring, an AI vision-language model "AIVI-Learning" now powered by Google Gemini Robotics, and a "Site View" of 360° imagery with mission authoring). It doubles as a digitalization layer (historical site catalogue, digital twin, laser scanning, CMMS/WMS integration via APIs, webhooks, and low-code work-order generation). Notably flexible on deployment: **Cloud (AWS-hosted), on-prem Site Hub (1U rack), or Virtual Machine**; enterprise-grade with SSO, multi-site, and SOC 2 Type II. Evidence is strongly Confirmed (detailed product page). The clear caveat: it manages BD hardware only.

**UI quality impression (subjective):** highly polished — map-based dashboards, performance dashboards, and a 360° Site View; among the most mature inspection UIs here. Real screenshots are on the product page.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Reliability / facility teams · operators"]

  subgraph UI["ORBIT WEB — dashboards · map · Site View"]
    UIM["Mission authoring · inspection review · alerts · performance"]
  end

  subgraph CORE["ORBIT PLATFORM — Cloud (AWS) / Site Hub (on-prem) / VM"]
    direction LR
    FM["Fleet mgmt:<br/>missions · scheduling"]
    INS["Inspection:<br/>visual/acoustic/thermal"]
    AIV["AIVI-Learning<br/>(Gemini VLM)"]
    DT["Digital twin /<br/>Site View"]
    FM ~~~ INS ~~~ AIV ~~~ DT
  end

  subgraph EXT["SYSTEMS OF RECORD"]
    CMMS["CMMS / WMS · APIs · webhooks · work orders"]
  end

  subgraph FLEET["BOSTON DYNAMICS ROBOTS (own hardware)"]
    ROB["Spot · Stretch · (Atlas)"]
  end

  OP --> UI
  UI --> CORE
  CORE <-->|"APIs · low-code work orders"| CMMS
  CORE <-->|"missions · data · teleop"| ROB

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style EXT fill:#ECFCCB,stroke:#65A30D,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((Orbit))
    Robot and Hardware Support
      Spot Stretch Atlas
      Own hardware only
    Fleet Management
      Mission editing
      Scheduling
      Map dashboard
      Remote operation
      Multi-site fleet health
    Inspection Intelligence
      Visual acoustic thermal
      Anomaly alerts
      Remote authoring
      AIVI VLM Gemini
      Site View 360
    Digital Twin and Data
      Site catalogue
      Laser scanning
      Site documentation
    Integration
      APIs webhooks
      Work order generation
      CMMS WMS
    Enterprise
      SSO
      Multi-site
      SOC2 Type II
    Deployment
      Cloud AWS
      Site Hub on-prem
      Virtual machine
    User Interface
      Map dashboards
      Performance dashboards
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("Orbit"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["Spot / Stretch / Atlas"]
  G1 --> G1b["Own hardware only"]

  R --> G2["2 · Fleet Management"]
  G2 --> G2a["Mission editing"]
  G2 --> G2b["Scheduling"]
  G2 --> G2c["Map-based dashboard"]
  G2 --> G2d["Remote operation"]
  G2 --> G2e["Multi-site fleet health"]

  R --> G3["3 · Inspection Intelligence"]
  G3 --> G3a["Visual / acoustic / thermal"]
  G3 --> G3b["Automated anomaly alerts"]
  G3 --> G3c["Remote inspection authoring"]
  G3 --> G3d["AIVI-Learning (Gemini VLM)"]
  G3 --> G3e["Site View 360"]

  R --> G4["4 · Digital Twin and Data"]
  G4 --> G4a["Historical site catalogue"]
  G4 --> G4b["Laser scanning"]
  G4 --> G4c["Site documentation"]

  R --> G5["5 · Integration"]
  G5 --> G5a["APIs / webhooks"]
  G5 --> G5b["Low-code work-order generation"]
  G5 --> G5c["CMMS / WMS"]

  R --> G6["6 · Enterprise"]
  G6 --> G6a["SSO"]
  G6 --> G6b["Multi-site"]
  G6 --> G6c["SOC 2 Type II"]

  R --> G7["7 · Deployment"]
  G7 --> G7a["Cloud (AWS)"]
  G7 --> G7b["Site Hub (on-prem 1U)"]
  G7 --> G7c["Virtual Machine"]

  R --> G8["8 · User Interface"]
  G8 --> G8a["Map dashboards"]
  G8 --> G8b["Performance dashboards"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Boston Dynamics robots** — Spot, Stretch, eventually Atlas [C]
- **1.2 Vendor-agnostic?** — No; BD hardware only [C]

### 2. Fleet Management
- **2.1 Mission editing & scheduling** [C]
- **2.2 Map-based dashboard** [C]
- **2.3 Remote robot operation** [C]
- **2.4 Performance summaries** [C]
- **2.5 Multi-site centralized dashboards / fleet health** [C]

### 3. Inspection Intelligence
- **3.1 Inspection data types** [C]
  - 3.1.1 Visual [C]
  - 3.1.2 Acoustic (air-leak detection) [C]
  - 3.1.3 Thermal (hotspots/anomalies) [C]
- **3.2 Anomaly alerting** — automated in-product + email; trend tracking [C]
- **3.3 Remote inspection authoring/editing** [C]
- **3.4 AI vision-language model — AIVI-Learning** (Google Gemini Robotics) [C]
- **3.5 Site View** — 360° imagery, condition history, mission authoring from imagery [C]

### 4. Digital Twin & Data
- **4.1 Facility digitalization** — historical visual catalogue [C]
- **4.2 Laser scanning** [C]
- **4.3 Site documentation / construction progress** [C]

### 5. Integration
- **5.1 APIs** [C]
- **5.2 Webhooks** [C]
- **5.3 Low-code work-order generation (beta)** [C]
- **5.4 CMMS / WMS / systems of record** [C]

### 6. Enterprise & Security
- **6.1 Customizable user profiles** [C]
- **6.2 SSO** [C]
- **6.3 Multi-site view** [C]
- **6.4 SOC 2 Type II certified** [C]

### 7. Deployment & Architecture
- **7.1 Cloud** — AWS-hosted (WiFi/LTE to Spot) [C]
- **7.2 Site Hub** — 1U rack-mounted on-prem appliance [C]
- **7.3 Virtual Machine** — OVA for VMware/Hyper-V/Azure/GCP [C]

### 8. User Interface & UX
- **8.1 Map-based dashboards** [C]
- **8.2 Performance dashboards** [C]
- **8.3 Site View (360°)** [C]

### 9. Connectivity & Protocols
- **9.1 Spot SDK / developer APIs** [C]
- **9.2 VDA5050/ROS** — not the integration model (BD-native) [I]

#### UI Screenshots
![Orbit overview](https://bostondynamics.com/wp-content/uploads/2025/05/what-is-orbit-1654x1370-1.png)
![Spot on Orbit map](https://bostondynamics.com/wp-content/uploads/2025/05/Spot-Orbit-map.png)
![Orbit performance dashboards](https://bostondynamics.com/wp-content/uploads/2026/04/Orbit-Performance-Dashboards.png)

**Inspection data trends (acoustic, with trend lines)**
![Orbit data trends](https://bostondynamics.com/wp-content/uploads/2025/05/data-trends-orbit-1280x1230-1.jpg)

**Stretch performance dashboard in Orbit**
![Orbit Stretch dashboard](https://bostondynamics.com/wp-content/uploads/2026/04/orbit-stretch-visual-1280x1230-1.png)

---

> **Gaps / to verify:** scheduling recurrence specifics, exact API surface, and whether any third-party robot support is planned (currently BD-only). Strong inspection benchmark. Confirm via Orbit release notes / a demo.

## Sources
- bostondynamics.com/products/orbit; bostondynamics.com/whitepaper/* ; dev.bostondynamics.com
