# Robot Fleet Management Systems (FMS) — Landscape & Index

*A survey of robot fleet-management software, organized by use-case domain. Each domain links to a domain analysis and to the per-product feature analyses.*

> Focuses on the **FMS software layer**, regardless of company's core business is robot hardware, system integration, navigation tech, or dedicated FMS.


## COTS FMS Domains:


Each domain analysis aggregates 4 products; each product's feature analysis has full detail, diagrams, evidence tags, and UI screenshots.

- Generic FMS
- Security & Patrol FMS
- Inspection FMS
- Warehouse FMS

---

## 1. Generic FMS Products
*Hardware-independent FMS that manage mixed fleets across brands and form factors. Broadest feature sets.*

📊 **[Generic Domain Analysis](./Generic/_Generic_Domain_Analysis.md)** (overview · reference architecture · aggregated features)

| # | Product | Analysis | Folder | Notes |
|---|---|---|---|---|
| 1 | **InOrbit** | [📄](./Generic/InOrbit/Feature_Analysis.md) | [📁](./Generic/InOrbit/) | Leading vendor-agnostic orchestration ("RobOps"); robots + people + IoT. US |
| 2 | **Formant** | [📄](./Generic/Formant/Feature_Analysis.md) | [📁](./Generic/Formant/) | Data/observability + teleop; now AI incident mitigation. US |
| 3 | **Meili Robots** | [📄](./Generic/Meili/Feature_Analysis.md) | [📁](./Generic/Meili/) | Universal, standards-native (ROS/VDA5050/MQTT); source-code license. Denmark |
| 4 | **Rapyuta Robotics** | [📄](./Generic/Rapyuta%20Robotics/Feature_Analysis.md) | [📁](./Generic/Rapyuta%20Robotics/) | Cloud-robotics DevOps + multi-robot coordination (ALICA). Japan |

*Other notable: MOV.AI, KINEXON Fleet Manager, Cogniteam, Freedom Robotics.*

---

## 2. Security & Patrol FMS Products
*Autonomous guarding, patrol routing, intrusion/fire/anomaly detection, and security operations consoles.*

📊 **[Security Domain Analysis](./Security/_Security_Domain_Analysis.md)**

| # | Product | Analysis | Folder | Notes |
|---|---|---|---|---|
| 1 | **Knightscope** | [📄](./Security/Knightscope/Feature_Analysis.md) | [📁](./Security/Knightscope/) | ASRs + mature KSOC console; RaaS, own hardware. US |
| 2 | **ugo** | [📄](./Security/ugo/Feature_Analysis.md) | [📁](./Security/ugo/) | Avatar robots + platform managing 3rd-party robots & CCTV; +inspection. Japan |
| 3 | **DOGU** | [📄](./Security/DOGU/Feature_Analysis.md) | [📁](./Security/DOGU/) | Patrover + edge-AI + SOS monitoring + Planner. South Korea |
| 4 | **Ascento** | [📄](./Security/Ascento/Feature_Analysis.md) | [📁](./Security/Ascento/) | Outdoor guard robot + app; turnkey RaaS, VMS-integrated. Switzerland |

*Other notable: SMP Robotics.*

---

## 3. Inspection & Field Robotics FMS Products
*Industrial asset inspection, autonomous missions, multi-modal data capture and insight; unstructured/outdoor environments.*

📊 **[Inspection Domain Analysis](./Inspection/_Inspection_Domain_Analysis.md)**

| # | Product | Analysis | Folder | Notes |
|---|---|---|---|---|
| 1 | **Boston Dynamics Orbit** | [📄](./Inspection/Boston%20Dynamics%20Orbit/Feature_Analysis.md) | [📁](./Inspection/Boston%20Dynamics%20Orbit/) | Orchestration + facility intelligence (Spot/Stretch); AIVI VLM; cloud/on-prem/VM. US |
| 2 | **FieldAI** | [📄](./Inspection/FieldAI/Feature_Analysis.md) | [📁](./Inspection/FieldAI/) | Hardware-agnostic autonomy "brain" + emerging security/insight product. US |
| 3 | **ANYbotics** | [📄](./Inspection/ANYbotics/Feature_Analysis.md) | [📁](./Inspection/ANYbotics/) | ANYmal legged inspection + Data Navigator analytics. Switzerland |
| 4 | **Energy Robotics (Korial)** | [📄](./Inspection/Energy%20Robotics/Feature_Analysis.md) | [📁](./Inspection/Energy%20Robotics/) | Hardware-agnostic; unifies robots + drones + cameras; digital twin. Germany |

*Other notable: Innovation Union (创联科技), dConstruct Robotics, Deep Robotics, QuadRobotics, Flotilla (Equinor, open-source).*

---

## 4. Warehouse & Logistics (AMR / AGV) FMS
*The most mature traffic-management, task-allocation, charging, and WMS/ERP integration. VDA 5050 is the key interoperability standard.*

📊 **[Warehouse Domain Analysis](./Warehouse/_Warehouse_Domain_Analysis.md)**

| # | Product | Analysis | Folder | Notes |
|---|---|---|---|---|
| 1 | **OTTO Motors (Rockwell)** | [📄](./Warehouse/OTTO%20Motors/Feature_Analysis.md) | [📁](./Warehouse/OTTO%20Motors/) | AMR fleet manager; MES/ERP/WMS API + PLC OPC-UA; VDA5050. Canada |
| 2 | **MiR Fleet** | [📄](./Warehouse/MiR%20Fleet/Feature_Analysis.md) | [📁](./Warehouse/MiR%20Fleet/) | Centralized MiR AMR control; REST API + VDA5050 adapter. Denmark (Teradyne) |
| 3 | **BlueBotics** | [📄](./Warehouse/BlueBotics/Feature_Analysis.md) | [📁](./Warehouse/BlueBotics/) | ANT navigation + ANT server fleet; VDA5050 multi-vendor. Switzerland |
| 4 | **SYNAOS** | [📄](./Warehouse/SYNAOS/Feature_Analysis.md) | [📁](./Warehouse/SYNAOS/) | Cloud-native, vendor-agnostic, VDA5050-native modular platform. Germany |

*Other notable: Geek+, Kollmorgen NDC/AMS, Seegrid, Vecna Polaris, KUKA, ABB, Omron, Standard Robots, Iplusmobot (迦智科技), Sunspeed (山速).*

---

## other vendors noted (not analyzed)
*Additional vendors identified during the survey, candidates for a future analyze.*

| Vendor | Likely domain | Note |
|---|---|---|
| **Innovation Union (创联科技)** | Inspection (heterogeneous cluster control) | Strong "heterogeneous coordination" story |
| **dConstruct Robotics** | Inspection / field | Construction, oil & gas, smart buildings (d.ASH Ops) |
| **Deep Robotics** | Inspection / patrol | Quadruped maker with bundled fleet software |
| **Pangolin Robot (穿山甲)** | Service / commercial robots | Commercial service-robot maker |

---

## Quick Observations
- **Breadth vs. depth:** the widest feature sets sit in **Generic** (vendor-agnostic) and **Warehouse** (AMR) : both matured over many deployment cycles. **Security** and **Inspection** add domain-specific detection, patrol/mission, and SOC/insight features.
- **Interoperability:** **VDA 5050** is the dominant cross-vendor standard, relevant for Warehouse, running one console over mixed robot brands. But among the Generic top-4, only **Meili** is VDA5050-native.
- **Heterogeneous coordination** (different robot types cooperating) is a genuine differentiator : in **InOrbit**, **Formant**, **ugo**, and **Korial**.
- **Deployment control:** **Meili** (source-code/self-host) and **Boston Dynamics Orbit** (cloud/on-prem/VM) offer the most deployment flexibility, and relevant for secure/air-gapped sites.

---

