# BlueBotics — Feature Analysis

**Product:** ANT navigation technology + ANT server (fleet manager) + ANT lab (config)
**Domain:** Warehouse & intralogistics — navigation tech + fleet management (vendor-agnostic via VDA5050)
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** · **[L] Likely** · **[I] Inferred**.

---

## Research & Summary

BlueBotics (Switzerland, a ZAPI Group company) is a **vehicle-navigation partner**: it provides **ANT** (Autonomous Navigation Technology) and **ANT server**, its mission/fleet-management software, for AGVs, automated forklifts, AMRs, and service robots. Its scale is notable — 6,000+ ANT-driven vehicles, 2,000+ installations, 150+ vehicle types automated — and ANT server adds **VDA5050** support so it can manage not only ANT-driven vehicles but also VDA5050-compliant AGVs/AMRs from non-ANT brands (vendor-agnostic reach). The ANT stack spans navigation (natural-feature, ±1 cm/±1°, minimal infrastructure, fast commissioning), configuration/mapping (**ANT lab**), localization variants (ANT lite+, localization/+, locator, outdoor GNSS), and fleet orchestration (mission/order management, traffic control, routing). It is primarily a navigation+fleet layer that integrators embed into vehicles, not a turnkey security/inspection product. Evidence is Confirmed at the capability level (website); deep operator-UI specifics are thinner.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Integrators / operators"]

  subgraph UI["ANT lab (config/mapping) + ANT server (fleet) UI"]
    UIM["Mapping · mission/order mgmt · traffic monitoring"]
  end

  subgraph CORE["ANT PLATFORM"]
    direction LR
    NAV["ANT navigation<br/>(natural feature)"]
    SRV["ANT server<br/>(fleet manager)"]
    LAB["ANT lab<br/>(config/mapping)"]
    NAV ~~~ SRV ~~~ LAB
  end

  subgraph FLEET["MIXED VEHICLE FLEET"]
    ANTV["ANT-driven AGVs / forklifts / AMRs"]
    VDA["VDA5050 vehicles (non-ANT brands)"]
  end

  OP --> UI
  UI --> CORE
  CORE <-->|"navigation + orders"| ANTV
  CORE <-->|"VDA5050"| VDA

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((BlueBotics ANT))
    Robot and Hardware Support
      AGVs forklifts AMRs
      ANT-driven vehicles
      VDA5050 non-ANT brands
    ANT Navigation
      Natural feature nav
      High precision
      Minimal infrastructure
      Outdoor GNSS
    ANT server Fleet
      Mission order mgmt
      Traffic control
      Routing
    ANT lab Config
      Mapping
      Vehicle commissioning
    Interoperability
      VDA5050
    User Interface
      ANT lab and server UI
    Deployment
      On-prem fleet server
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("ANT"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["AGVs / forklifts / AMRs / service robots"]
  G1 --> G1b["ANT-driven vehicles (6000+)"]
  G1 --> G1c["VDA5050 non-ANT brands"]

  R --> G2["2 · ANT Navigation"]
  G2 --> G2a["Natural-feature navigation"]
  G2 --> G2b["High precision (1cm/1deg)"]
  G2 --> G2c["Minimal infrastructure"]
  G2 --> G2d["Outdoor GNSS"]

  R --> G3["3 · ANT server (fleet)"]
  G3 --> G3a["Mission / order management"]
  G3 --> G3b["Traffic control"]
  G3 --> G3c["Routing"]

  R --> G4["4 · ANT lab (config)"]
  G4 --> G4a["Mapping"]
  G4 --> G4b["Vehicle commissioning"]

  R --> G5["5 · Interoperability"]
  G5 --> G5a["VDA5050"]

  R --> G6["6 · User Interface"]
  G6 --> G6a["ANT lab + ANT server UI"]

  R --> G7["7 · Deployment"]
  G7 --> G7a["On-prem fleet server"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Vehicle types** — AGVs, automated forklifts, AMRs, service robots [C]
- **1.2 ANT-driven vehicles** — 6,000+ in operation, 150+ vehicle types [C]
- **1.3 Vendor-agnostic via VDA5050** — manage non-ANT brands [C]

### 2. ANT Navigation
- **2.1 Natural-feature navigation** [C]
  - 2.1.1 Accuracy ±1 cm / ±1° [C]
  - 2.1.2 Minimal infrastructure changes [C]
  - 2.1.3 Fast commissioning (days) [C]
- **2.2 Localization variants** — ANT lite+, ANT localization/+, ANT locator [C]
- **2.3 Outdoor GNSS navigation** [C]

### 3. ANT server (Fleet Manager)
- **3.1 Mission / order management** [C]
- **3.2 Traffic control** [C]
- **3.3 Routing across mixed vehicles** [C]

### 4. ANT lab (Configuration)
- **4.1 Mapping / routing setup** [C]
- **4.2 Vehicle commissioning** [C]

### 5. Interoperability
- **5.1 VDA5050 support** — manage ANT + non-ANT VDA5050 vehicles [C]

### 6. User Interface & UX
- **6.1 ANT lab (config) + ANT server (fleet) interfaces** [C]
- **6.2 Map-based** [L]

### 7. Deployment & Architecture
- **7.1 On-prem fleet server** [L]
- **7.2 Cloud option** — not confirmed [I]

### 8. Connectivity & Protocols
- **8.1 VDA5050** [C]
- **8.2 API / integration** [L]

### 9. Commercial Model
- **9.1 Navigation technology + fleet software licensing** (for OEMs/integrators) [L]

#### UI Screenshots

**Ant lab software overview**
![Ant lab software overview](Images/ui_ant-lab-software-overview.jpg)

**Ant lab step1 configure vehicle**
![Ant lab step1 configure vehicle](Images/ui_ant-lab-step1-configure-vehicle.jpg)

**Ant lab step2 calibrate laser**
![Ant lab step2 calibrate laser](Images/ui_ant-lab-step2-calibrate-laser.jpg)

**Ant lab step3 create map**
![Ant lab step3 create map](Images/ui_ant-lab-step3-create-map.jpg)

**Ant lab step4 define routes**
![Ant lab step4 define routes](Images/ui_ant-lab-step4-define-routes.jpg)

**Ant lab step5 define actions**
![Ant lab step5 define actions](Images/ui_ant-lab-step5-define-actions.jpg)

**Ant lab step6 test project**
![Ant lab step6 test project](Images/ui_ant-lab-step6-test-project.jpg)

**Ant lab2 actions**
![Ant lab2 actions](Images/ui_ant-lab2-actions.png)

**Agv control system**
![Agv control system](Images/arch_agv-control-system.png)

**Ant compatibility**
![Ant compatibility](Images/arch_ant-compatibility.png)

**Ant lite system integration**
![Ant lite system integration](Images/arch_ant-lite-system-integration.png)

---

> **Gaps / to verify:** ANT server operator-UI/scheduling detail, cloud vs on-prem, charging management, security/RBAC, and pricing. Confirm via the ANT server datasheet or a demo. Integrator-oriented navigation+fleet layer, not turnkey security/inspection.

## Sources
- bluebotics.com (home, ANT server, ANT navigation)
