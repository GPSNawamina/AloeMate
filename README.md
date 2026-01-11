# 🌿 AloeMate — AI-Powered Smart Farming Platform for Aloe Vera
**AloeMate** is an AI-powered smart farming platform for **Aloe Vera disease/defect detection, forecasting, and smart utilization**.  
It combines **Computer Vision + IoT + Conversational AI + Market Trend Analytics** to support farmers with **early detection, prevention, treatment guidance, and optimal harvest timing**.

---

## 🔗 Repository
- GitHub: https://github.com/GPSNawamina/AloeMate.git

---

## 🧾 Table of Contents
- [Project Name + Short Description](#-project-name--short-description)
- [Project Overview](#-project-overview)
- [Problem Statement](#-problem-statement)
- [Project Objectives](#-project-objectives)
- [Expected Outcomes](#-expected-outcomes)
- [System Components](#-system-components)
  - [Component 1: Disease/Defect Detection + Treatment Guidance](#component-1-diseasedefect-detection--treatment-guidance)
  - [Component 2: IoT Monitoring + Disease Risk Alerts](#component-2-iot-monitoring--disease-risk-alerts)
  - [Component 3: AI Chatbot + Treatment Scheduler](#component-3-ai-chatbot--treatment-scheduler)
  - [Component 4: Market Trend–Based Harvest Predictor](#component-4-market-trendbased-harvest-predictor)
- [Accessibility & Inclusive Design](#-accessibility--inclusive-design)
- [System Architecture](#-system-architecture)
  - [Architectural Diagram (High Level)](#-architectural-diagram-high-level)
- [Technologies Used](#-technologies-used)
- [Requirements / Dependencies](#-requirements--dependencies)
- [Project Structure](#-project-structure)
- [Configuration](#-configuration)
  - [Backend `.env`](#backend-env)
  - [Mobile `.env`](#mobile-env)
  - [IoT `.env` / config](#iot-env--config)
- [Setup Instructions](#-setup-instructions)
- [How to Run](#-how-to-run)
- [How to Test](#-how-to-test)
- [Deployment Notes](#-deployment-notes)
- [Other Dependencies (External Services)](#-other-dependencies-external-services)
- [Git Workflow: Commits, Branches, Merges](#-git-workflow-commits-branches-merges)
- [Demo Link / Credentials](#-demo-link--credentials)
- [Contributors](#-contributors)
- [License](#-license)

---

## ✨ Project Name + Short Description
**AloeMate** is a smart farming platform that helps Aloe Vera growers:
- Detect diseases/defects early using AI vision models
- Predict disease risk using IoT microclimate monitoring
- Receive multilingual chatbot-based guidance and reminders
- Predict best harvest time using maturity + market trends

---

## 📌 Project Overview
Aloe Vera cultivation often suffers from delayed diagnosis, poor access to expert advice, and non-optimal harvest timing. AloeMate integrates four components into a single decision-support system:

- **Mobile AI Disease Detection** (multi-photo + confidence-based results)
- **IoT Monitoring** (temperature/humidity/soil moisture + early risk alerts)
- **Chatbot + Scheduler** (voice/text + treatment reminders)
- **Harvest Predictor** (maturity prediction + market-aligned harvest window)

This platform is designed to be **mobile-first**, **farmer-friendly**, and expandable to additional crops in the future.

---

## ❗ Problem Statement
Farmers often rely on visual inspection and manual experience:
- Diseases are detected late → yield loss and low quality
- Lack of microclimate monitoring → no early warning signals
- Advice is fragmented and not personalized (scientific vs traditional)
- Harvest timing decisions are often subjective and not aligned with market trends

AloeMate solves these issues by combining **AI + IoT + conversational guidance + market trend analytics** into one integrated platform.

---

## 🎯 Project Objectives
### Main Objective
Develop a holistic AI-integrated system to support Aloe Vera farmers in Sri Lanka with **disease management, forecasting, treatment support, and harvest optimization**.

### Specific Objectives
- Detect diseases/defects using **mobile-friendly computer vision**
- Forecast disease risk using **IoT microclimate monitoring**
- Provide treatment recommendations via an **AI chatbot** with voice/text input
- Convert treatment guidance into **schedules & reminders**
- Predict harvest readiness using **maturity models + market demand trends**
- Improve usability through **accessibility and inclusive design**

---

## ✅ Expected Outcomes
- Early disease identification and reduced crop loss
- Preventive disease alerts before visible symptoms
- Higher farmer confidence through step-by-step treatments
- Improved adherence through scheduling and reminders
- Better harvest timing decisions → improved profitability
- Strong foundation for scaling to additional crops and regions

---

## 🧩 System Components

### Component 1: Disease/Defect Detection + Treatment Guidance
**Goal:** Detect Aloe Vera diseases/defects from field images and provide confidence-based treatment guidance.

**Features**
- Multi-photo capture (close-up / whole plant / base/soil)
- AI inference (CNN-based model; mobile-optimized)
- Image quality validation (blur/brightness checks)
- Top-3 predictions with calibrated confidence
- Scientific + Ayurvedic treatment plans with steps, duration, safety notes

---

### Component 2: IoT Monitoring + Disease Risk Alerts
**Goal:** Provide early-warning disease prediction using environmental thresholds.

**Features**
- IoT sensors: temperature, humidity, soil moisture
- Daily average calculation
- Rule-based disease threshold comparison
- Risk classification: Low / Medium / High
- SMS/WhatsApp alerts in Sinhala/English
- Cloud storage & multi-location monitoring

---

### Component 3: AI Chatbot + Treatment Scheduler
**Goal:** Enable farmers to describe symptoms (voice/text) and receive personalized guidance with reminders.

**Features**
- Text + voice symptom reporting (ASR + NLP)
- Intent detection + Named Entity Recognition (NER)
- Aloe-specific knowledge base (scientific + traditional)
- Context memory for follow-up conversations
- Treatment scheduling and reminder management

---

### Component 4: Market Trend–Based Harvest Predictor
**Goal:** Predict optimal harvest time based on plant maturity + market prices.

**Features**
- Two-stage pipeline:
  - CNN classifier: Preliminary / Intermediate / Mature
  - Regression model: days-to-maturity for intermediate stage
- Integrates real-time market trend data via APIs
- Product-specific recommendations (gel/juice/pharma)
- Mobile-first decision support dashboard

---

## ♿ Accessibility & Inclusive Design

### 👁️ Visual Impairment Support
- Screen-reader friendly structure
- Large text scaling compatibility
- High-contrast friendly UI patterns
- (Future) voice narration for results/treatments

### 👂 Hearing Impairment Support
- All key information displayed as text
- Visual confirmations and alerts
- (Future) haptic feedback for alerts

### 🧠 Cognitive & Learning Difficulties Support
- Step-by-step guidance with checklists
- Confidence-based decision flow
- Consistent navigation with minimal clutter UI
- Clear badges and progress indicators

---

## 🏗️ System Architecture

### 📐 Architectural Diagram (High Level)
```mermaid
flowchart LR
  Farmer((Farmer)) --> Mobile[Mobile App\nReact Native + Expo]

  subgraph M1[Component 1: Disease/Defect Detection + Treatment]
    Mobile --> Capture[Multi-Photo Capture\n(1-3 images)]
    Capture --> QC[Image Quality Checks\n(blur/brightness)]
    QC --> Model[AI Inference\nCNN / PyTorch / TFLite]
    Model --> Calib[Calibration\nTemperature Scaling]
    Calib --> Top3[Top-3 Predictions + Confidence]
    Top3 --> Treat[Treatment Guidance\nScientific + Ayurvedic]
  end

  subgraph M2[Component 2: IoT Monitoring + Disease Risk Alerts]
    Sensors[IoT Sensors\nTemp/Humidity/Soil Moisture] --> Edge[ESP32 Device]
    Edge --> Cloud[Cloud Storage/Processing]
    Cloud --> Risk[Risk Classification\nLow/Med/High]
    Risk --> Alerts[SMS/WhatsApp Alerts\nSinhala/English]
  end

  subgraph M3[Component 3: AI Chatbot + Scheduler]
    Mobile --> Chat[Voice/Text Chat UI]
    Chat --> NLP[NLP + ASR + NER]
    NLP --> KB[Knowledge Base\nScientific + Traditional]
    KB --> Rec[Recommendations]
    Rec --> Sched[Treatment Scheduling + Reminders]
  end

  subgraph M4[Component 4: Harvest Predictor + Market Trends]
    Mobile --> HImg[Maturity Image Input]
    HImg --> StageCls[CNN Classifier\nPre/Inter/Mature]
    StageCls --> Reg[Regression\nDays-to-Maturity]
    MarketAPI[Market Price API] --> Market[Market Trend Analyzer]
    Reg --> Harvest[Optimal Harvest Window]
    Market --> Harvest
  end

  Treat --> Mobile
  Alerts --> Mobile
  Sched --> Mobile
  Harvest --> Mobile
