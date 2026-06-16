# SYNAOS — Feature Analysis

**Product:** SYNAOS Intralogistics Management Platform (IMP) — incl. Mobile Robot Fleet Management
**Domain:** Warehouse & intralogistics — **vendor-agnostic** material-flow orchestration
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** · **[L] Likely** · **[I] Inferred**.

---

## Research & Summary

SYNAOS (Germany) offers the **Intralogistics Management Platform (IMP)** — an "all-in-one / one-for-all" control center that orchestrates **every transport resource** (AMRs, AGVs, forklifts, and people) from one cloud-native, **vendor-agnostic** platform built natively on **VDA5050**. Its headline module is **Mobile Robot Fleet Management** (manufacturer-independent control of mixed AMR/AGV fleets via VDA5050, with the industry's largest partner network — 40+ robot makers), surrounded by **Forklift Guidance**, **Real-Time Localization**, **Warehouse Execution** (buffer/inventory), **Vehicle & Operator Management**, **Asset Control**, **Order & Process Management**, **Storage Management**, and **Digital Twin & Simulation**. Smart algorithms always assign the best resource per job; it's cloud-native (on AWS), highly available, and **ISO 27001 + TISAX** certified. Proof points: the largest VDA5050 fleet in industry (130+, at VW Commercial Vehicles), 50+ live installs, 10k+ daily orders. Among the strongest *truly* vendor-agnostic, standards-based fleet managers in the survey — but oriented to intralogistics/material flow, not security/inspection. Evidence is strongly Confirmed (detailed platform site).

**UI quality impression (subjective):** enterprise "control center" with a clean platform UI (IMP); a real laptop/dashboard image is on the site.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Plant / logistics operators"]

  subgraph UI["SYNAOS IMP — control center"]
    UIM["Orchestration · localization · execution · digital twin"]
  end

  subgraph CORE["INTRALOGISTICS MANAGEMENT PLATFORM (cloud-native, AWS)"]
    direction LR
    MRFM["Mobile Robot<br/>Fleet Mgmt (VDA5050)"]
    FORK["Forklift<br/>Guidance"]
    RTLS["Real-Time<br/>Localization"]
    WE["Warehouse<br/>Execution"]
    DT["Digital Twin<br/>& Simulation"]
    MRFM ~~~ FORK ~~~ RTLS ~~~ WE ~~~ DT
  end

  subgraph FLEET["VENDOR-AGNOSTIC RESOURCES"]
    ROB["AMRs · AGVs (40+ makers, VDA5050)"]
    HUM["Forklifts + human operators"]
  end

  OP --> UI
  UI --> CORE
  CORE <-->|"VDA5050"| ROB
  CORE <-->|"guidance / localization"| HUM

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((SYNAOS IMP))
    Robot and Hardware Support
      Vendor-agnostic
      AMRs AGVs forklifts people
      VDA5050 native
      40+ robot partners
    Mobile Robot Fleet Mgmt
      Manufacturer-independent
      Mixed fleet orchestration
    Forklift Guidance
      Digitize forklift workflows
    Real-Time Localization
      Sensor kits
      Shopfloor transparency
    Warehouse Execution
      Buffer management
      Inventory management
    Vehicle and Operator Mgmt
      Humans trucks robots
    Asset and Order Mgmt
      Asset control
      Order optimization
    Digital Twin
      Simulation
    Security
      ISO 27001 TISAX
    Deployment
      Cloud-native AWS
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("SYNAOS IMP"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["Vendor-agnostic"]
  G1 --> G1b["AMRs / AGVs / forklifts / people"]
  G1 --> G1c["VDA5050 native"]
  G1 --> G1d["40+ robot partners"]

  R --> G2["2 · Mobile Robot Fleet Mgmt"]
  G2 --> G2a["Manufacturer-independent control"]
  G2 --> G2b["Mixed fleet orchestration"]

  R --> G3["3 · Forklift Guidance"]
  G3 --> G3a["Digitize forklift workflows"]

  R --> G4["4 · Real-Time Localization"]
  G4 --> G4a["Plug-and-play sensor kits"]
  G4 --> G4b["Shopfloor transparency"]

  R --> G5["5 · Warehouse Execution"]
  G5 --> G5a["Buffer management"]
  G5 --> G5b["Inventory management"]

  R --> G6["6 · Vehicle & Operator Mgmt"]
  G6 --> G6a["Humans + trucks + robots"]

  R --> G7["7 · Asset & Order Mgmt"]
  G7 --> G7a["Asset Control"]
  G7 --> G7b["Order & Process Mgmt"]
  G7 --> G7c["Storage Management"]

  R --> G8["8 · Digital Twin"]
  G8 --> G8a["Simulation / emulation"]

  R --> G9["9 · Security"]
  G9 --> G9a["ISO 27001 + TISAX"]

  R --> G10["10 · Deployment"]
  G10 --> G10a["Cloud-native (AWS)"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Vendor-agnostic / manufacturer-independent** [C]
- **1.2 Resource types** — AMRs, AGVs, forklifts, and human operators [C]
- **1.3 VDA5050 native** [C]
- **1.4 Largest partner network** — 40+ mobile-robot makers [C]

### 2. Mobile Robot Fleet Management (MRFM)
- **2.1 Centralize & orchestrate mixed AMR/AGV fleets** [C]
- **2.2 Manufacturer-independent control via VDA5050** [C]
- **2.3 Holistic resource optimization** — assign best resource per job; cut idle/bottlenecks [C]

### 3. Forklift Guidance
- **3.1 Digitize manual forklift workflows** [C]
- **3.2 Reduce empty runs / idle time** [C]

### 4. Real-Time Localization
- **4.1 Plug-and-play sensor kits** — track every forklift/robot/pallet [C]
- **4.2 Shopfloor transparency** — detect delays, optimize routes [C]

### 5. Warehouse Execution
- **5.1 Buffer management** [C]
- **5.2 Inventory / load tracking** [C]

### 6. Vehicle & Operator Management
- **6.1 Combine human operators, industrial trucks, mobile robots (manufacturer-independent)** [C]

### 7. Asset, Order & Storage Management
- **7.1 Asset Control** — status + control of assets [C]
- **7.2 Order & Process Management** — order optimization [C]
- **7.3 Storage Management** — inventory/compliance [C]

### 8. Digital Twin & Simulation
- **8.1 Cloud-based facility replica** — model workflows, traffic, layout [C]
- **8.2 Test robot paths / buffer strategies before deployment** [C]

### 9. Security & Compliance
- **9.1 ISO 27001:2017 certified** [C]
- **9.2 TISAX assessment** [C]

### 10. Deployment & Architecture
- **10.1 Cloud-native (AWS), highly available** [C]
- **10.2 On-prem option** — not stated [I]

### 11. User Interface & UX
- **11.1 IMP control-center UI** [C]
- **11.2 Map / digital-twin views** [L]

### 12. Connectivity & Protocols
- **12.1 VDA5050** [C]
- **12.2 AWS-based integration; enterprise IT** [C]
- **12.3 REST/MQTT/OPC-UA specifics** — not enumerated [I]

#### UI Screenshots

**IMP control center (laptop)**
![SYNAOS IMP on laptop](https://cdn.prod.website-files.com/61fa39c3eda3ef38a97fde68/65e1f107e8caf496c9ba2995_SYNAOS_IMP_Laptop.jpg)

**Fleet management software screenshot**
![SYNAOS software screenshot](https://cdn.prod.website-files.com/61fa39c3eda3ef38a97fde68/62ac43bc329920704c0813b1_SYNA.OS%20LOGISTICS%20software%20screenshot.webp)

**Desktop console (traffic / tracking)**
![SYNAOS desktop console](https://cdn.prod.website-files.com/61fa39c3eda3ef38a97fde68/6284d678b766a6507040214b_desktop%20mockup%20-%20shadow.webp)

**Solutions / route-planning screen**
![SYNAOS solutions screen](https://cdn.prod.website-files.com/61fa39c3eda3ef38a97fde68/62a8e42399086f00ea0f4812_solutions1.webp)

---

> **Gaps / to verify:** detailed protocol surface beyond VDA5050, on-prem availability, scheduling/recurrence, RBAC/SSO, and pricing. Strong vendor-agnostic, standards-based benchmark. Confirm via synaos.com/platform or the on-demand demo. Intralogistics orientation (not security/inspection).

## Sources
- synaos.com/en (home, platform, MRFM)
