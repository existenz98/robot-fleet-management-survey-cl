# Knightscope — Feature Analysis

**Product:** KSOC (Knightscope Security Operations Center) + Autonomous Security Robots (ASRs)
**Domain:** Security & patrol (own-hardware RaaS)
**Analysis date:** 2026-06-12
**Sources:** vendor website and public product materials.
**Evidence legend:** **[C] Confirmed** = stated in official or vendor materials · **[L] Likely** = vendor marketing or strongly implied · **[I] Inferred** = deduced / not stated.

---

## Research & Summary

Knightscope is a US-listed (NASDAQ: KSCP) pure-play physical-security company whose fleet/operations layer is **KSOC — the Knightscope Security Operations Center**, a browser-based console included with every Autonomous Security Robot (ASR) subscription (a RaaS model). KSOC manages Knightscope's **own hardware** — K1 (stationary), K5 (outdoor mobile), K7 (multi-terrain) ASRs plus blue-light emergency devices and Automated Gunshot Detection — so it is *not* vendor-agnostic. Its strength is detection + investigation: live 360° HD video, people detection, facial recognition, thermal (fire/heat/concealed persons), and ALPR, all surfaced through a responsive desktop/tablet/mobile UI with time/location/detection filters across 240M+ delivered detections. It is a directly comparable Western peer for guarding use cases; depth is Confirmed for the KSOC feature set (official product page) but configuration-level details (alert rules, scheduling) aren't enumerated publicly and are tagged Likely/Inferred.

**UI quality impression (subjective):** polished, security-operations-center styling; responsive across devices with strong evidence/video review tooling. Real KSOC screenshots are available on the product page.

---

## System Architecture

```mermaid
%%{init: {"theme":"base","themeVariables":{"fontSize":"13px","primaryColor":"#EEF2F7","primaryBorderColor":"#64748B","primaryTextColor":"#0F172A","lineColor":"#64748B","clusterBkg":"#F8FAFC","clusterBorder":"#94A3B8","titleColor":"#0F172A","textColor":"#0F172A"}}}%%
flowchart TB
  OP["Security operators / clients<br/>(24/7/365)"]

  subgraph UI["KSOC — browser console (desktop · tablet · mobile)"]
    UIM["Live video · detections · investigation filters · alerts"]
  end

  subgraph CORE["KNIGHTSCOPE CLOUD — RaaS platform"]
    direction LR
    REC["Recording &<br/>streaming"]
    DET["Detection<br/>(people/face/thermal/ALPR)"]
    INV["Incident<br/>investigation"]
    COM["Two-way<br/>communication"]
    REC ~~~ DET ~~~ INV ~~~ COM
  end

  subgraph FLEET["KNIGHTSCOPE DEVICES (own hardware)"]
    ASR["ASRs: K1 · K5 · K7"]
    EMG["Blue-light towers/phones · Gunshot detection"]
  end

  OP --> UI
  UI --> CORE
  CORE <-->|"telemetry · video · commands"| ASR
  CORE <-->|"alerts / signals"| EMG

  style UI fill:#E0F2FE,stroke:#0284C7,color:#0F172A
  style CORE fill:#EDE9FE,stroke:#7C3AED,color:#0F172A
  style FLEET fill:#FFE4E6,stroke:#E11D48,color:#0F172A
```

---

## Feature Map (top 2 levels)

```mermaid
mindmap
  root((Knightscope KSOC))
    Robot and Hardware Support
      Own ASRs K1 K5 K7
      Emergency devices
      Not vendor-agnostic
    Monitoring and Streaming
      Live 360 HD video
      Recorded storage
      Evidence download
    Detection
      People detection
      Facial recognition
      Thermal
      ALPR
    Incident Investigation
      Time location filters
      Detection filters
    Communication
      Two-way comms
      Blue light devices
    Emergency Detection
      Gunshot detection
      KEMS
    User Interface
      Browser console
      Responsive devices
    Deployment and Commercial
      Cloud RaaS
      Subscription
    Security and Access
      Authorized users
```

### Alternative layout — grouped tree (cleaner)

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 16, "rankSpacing": 55, "useMaxWidth": true}, "themeVariables": {"fontSize": "11px"}}}%%
flowchart LR
  R(("KSOC"))

  R --> G1["1 · Robot and Hardware Support"]
  G1 --> G1a["Own ASRs (K1/K5/K7)"]
  G1 --> G1b["Emergency devices"]
  G1 --> G1c["Not vendor-agnostic"]

  R --> G2["2 · Monitoring and Streaming"]
  G2 --> G2a["Live 360 HD video"]
  G2 --> G2b["Recorded HD storage"]
  G2 --> G2c["Evidence download"]

  R --> G3["3 · Detection"]
  G3 --> G3a["People detection"]
  G3 --> G3b["Facial recognition"]
  G3 --> G3c["Thermal (fire/heat/concealed)"]
  G3 --> G3d["ALPR"]

  R --> G4["4 · Incident Investigation"]
  G4 --> G4a["Time/location filters"]
  G4 --> G4b["Detection filters"]

  R --> G5["5 · Communication"]
  G5 --> G5a["Two-way comms"]
  G5 --> G5b["Blue-light devices"]

  R --> G6["6 · Emergency Detection"]
  G6 --> G6a["Automated gunshot detection"]
  G6 --> G6b["KEMS"]

  R --> G7["7 · User Interface"]
  G7 --> G7a["Browser console"]
  G7 --> G7b["Responsive (desktop/tablet/mobile)"]

  R --> G8["8 · Deployment and Commercial"]
  G8 --> G8a["Cloud RaaS"]
  G8 --> G8b["Subscription (KSOC included)"]

  R --> G9["9 · Security and Access"]
  G9 --> G9a["Authorized-user access"]
```

---

## Feature List

### 1. Robot & Hardware Support
- **1.1 Own Autonomous Security Robots** [C]
  - 1.1.1 K1 Hemisphere (stationary) [C]
  - 1.1.2 K5 (outdoor mobile) [C]
  - 1.1.3 K7 (multi-terrain) [C]
- **1.2 Emergency communication devices** — blue-light towers, e-phones, call boxes [C]
- **1.3 Vendor-agnostic?** — No; KSOC manages Knightscope hardware only [C]

### 2. Monitoring & Streaming
- **2.1 Live video** — 360° HD [C]
- **2.2 Recorded HD video storage** [C]
- **2.3 Evidence export** — downloadable files [C]

### 3. Detection
- **3.1 People detection** [C]
  - 3.1.1 Off-hours detection [C]
  - 3.1.2 Restricted-area alerts [C]
- **3.2 Facial recognition** [C]
  - 3.2.1 VIP / key-person alerts [C]
  - 3.2.2 User-generated watchlists [C]
- **3.3 Thermal** [C]
  - 3.3.1 Fire detection [C]
  - 3.3.2 Vehicle heat blooms [C]
  - 3.3.3 People concealed in darkness [C]
- **3.4 ALPR (license plate recognition)** [C]
  - 3.4.1 Approved/denied plate lists [C]
  - 3.4.2 Parking monitoring [C]

### 4. Incident Investigation
- **4.1 Investigation tooling** [C]
  - 4.1.1 Filter by time / location / detection type [C]
  - 4.1.2 240M+ detections delivered (scale) [C]

### 5. Communication
- **5.1 Two-way communication** via ASR [C]
- **5.2 Blue-light emergency integration** [C]

### 6. Emergency Detection (related modules)
- **6.1 Automated Gunshot Detection (AGD)** [C]
- **6.2 Knightscope Emergency Management System (KEMS)** [C]
- **6.3 Risk & Threat Exposure (RTX) monitoring** [C]

### 7. User Interface & UX
- **7.1 Browser-based console** [C]
- **7.2 Responsive** — desktop / tablet / mobile [C]
- **7.3 3D/map operator view** — not detailed [I]

### 8. Deployment & Commercial
- **8.1 Cloud (RaaS)** — KSOC included with every subscription [C]
- **8.2 Hourly/subscription pricing** [L]

### 9. Security & Governance
- **9.1 Authorized-user access** [C]
- **9.2 SSO / RBAC specifics** — not stated [I]

#### UI Screenshots

**Agd screenshot**
![Agd screenshot](Images/ui_agd-screenshot.png)

**Kems console**
![Kems console](Images/ui_kems-console.jpg)

**Kems laptop mockup**
![Kems laptop mockup](Images/ui_kems-laptop-mockup.jpg)

**Ksoc desktop laptop**
![Ksoc desktop laptop](Images/ui_ksoc-desktop-laptop.jpg)

**Ksoc section**
![Ksoc section](Images/ui_ksoc-section.jpg)

**Msp platform screenshot**
![Msp platform screenshot](Images/ui_msp-platform-screenshot.png)

**Rtx security center**
![Rtx security center](Images/ui_rtx-security-center.png)

**Tech spec screenshot**
![Tech spec screenshot](Images/ui_tech-spec-screenshot.png)

**Asf escalation model**
![Asf escalation model](Images/arch_asf-escalation-model.jpg)

**Asf graphic**
![Asf graphic](Images/arch_asf-graphic.png)

**Msp one throat**
![Msp one throat](Images/diagram_msp-one-throat.png)

---

> **Gaps / to verify:** patrol-route scheduling/recurrence, alert-rule configuration, VMS/third-party integration, API availability, SSO/RBAC, and pricing specifics. Confirm via Knightscope spec sheets (knightscope.com/tech) or a demo. Note: own-hardware only — no multi-vendor management.

## Sources
- knightscope.com/products/ksoc, knightscope.com/tech (spec sheets)
