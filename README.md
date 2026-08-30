# RetinAI 👁️

**Explainable AI-Powered Diabetic Retinopathy Screening for Rural India**

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Smart India Hackathon 2026](https://img.shields.io/badge/SIH-2026-orange.svg)](https://sih.gov.in/)
[![Status](https://img.shields.io/badge/status-prototype-yellow.svg)]()

> One photo. One AI. One chance to save someone's vision.

---

## 📌 Table of Contents

- [Problem Statement](#-problem-statement)
- [Our Solution](#-our-solution)
- [Key Features](#-key-features)
- [Innovation & Uniqueness](#-innovation--uniqueness)
- [How It Works (Workflow)](#-how-it-works-workflow)
- [Technology Stack](#-technology-stack)
- [Feasibility](#-feasibility)
- [Viability](#-viability)
- [Potential Challenges & Risks](#-potential-challenges--risks)
- [Mitigation Strategies](#-mitigation-strategies)
- [Impact & Benefits](#-impact--benefits)
- [Alignment with National Missions](#-alignment-with-national-missions)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Team](#-team)
- [License](#-license)

---

## 🩺 Problem Statement

Diabetic retinopathy (DR) is one of the leading **preventable** causes of blindness among India's **77M+ diabetics** — yet it shows **zero symptoms** until vision damage has already begun.

- **Silent Onset** — Diabetic retinopathy causes no pain and no warning signs until it's often too late.
- **Limited Access** — Rural India has almost no ophthalmologists within reach for early screening.
- **Disconnected Care** — No link between screening, diagnosis, and specialist follow-up at the village level.

Screening requires a retinal specialist and a fundus camera — both scarce outside tier-1 cities — so patients go undiagnosed until vision loss is already severe and irreversible.

---

## 💡 Our Solution

RetinAI turns any smartphone into a diabetic retinopathy screening tool — no specialist required on the spot.

- **Smartphone-First Capture** — Just a phone and a low-cost clip-on retinal lens; no expensive fundus camera or specialist hardware needed.
- **On-Device AI Detection** — A fine-tuned **EfficientNet-B0** model grades DR severity instantly, right on the device.
- **Explain, Don't Just Predict** — A **Grad-CAM heatmap** overlays the exact region driving the AI's verdict, so the health worker sees and trusts the reasoning.
- **Triage, Not Diagnose** — Results sort into **Healthy / Monitor / Urgent Referral** — safe, actionable, never a false diagnosis.
- **Built for the Field** — Runs **fully offline** on-device, syncing to the cloud only when signal returns.

---

## ✨ Key Features

- 📸 Retinal image capture via smartphone + clip-on lens
- 🤖 On-device AI severity classification (EfficientNet-B0)
- 🔥 Grad-CAM visual explainability overlay
- 🚦 Three-tier triage banding (Healthy / Monitor / Urgent Referral)
- 📴 Offline-first capture with automatic batch sync
- 📊 Camp/clinic-level coordinator dashboard
- 🔗 ABDM-compatible record structure

---

## 🚀 Innovation & Uniqueness

| Feature | Why It Matters |
|---|---|
| **Self-Explaining AI** | Most tools give a verdict and expect trust. Ours shows its reasoning directly on the image, so the health worker can see what the AI saw. |
| **Triage, Not Diagnosis** | We never claim to diagnose. Sorting patients into Healthy, Monitor, or Urgent Referral keeps the tool safe, honest, and genuinely useful in the field. |
| **Offline-First by Design** | Built for the reality of rural connectivity, not against it. A full day's screenings run and save locally, syncing only when signal returns. |
| **Zero Extra Hardware** | No custom scanner, no proprietary device. It works on any smartphone camera a health worker already carries. |

---

## 🔄 How It Works (Workflow)

```
Capture → AI Analysis → Triage → Sync & Dashboard → Follow-up
```

1. **Capture** — Smartphone + clip-on lens photographs the patient's retina.
2. **AI Analysis** — On-device model grades DR severity and generates a Grad-CAM heatmap for explainability.
3. **Triage** — Result sorted into Healthy, Monitor, or Urgent Referral.
4. **Sync & Dashboard** — Screening saved offline, synced to cloud when signal returns, visible on coordinator dashboard.
5. **Follow-up** — Urgent cases forwarded to a specialist for confirmation.

---

## 🛠 Technology Stack

**AI / Machine Learning**
- PyTorch — model training and fine-tuning
- EfficientNet-B0 — DR severity classification
- Grad-CAM (`pytorch-grad-cam`) — visual explainability
- APTOS 2019 Dataset — training data
- OpenCV / PIL — image preprocessing (crop, normalize, blur-check)
- ONNX — model conversion for mobile deployment

**Mobile App**
- Flutter — cross-platform Android/iOS app
- TensorFlow Lite — on-device model inference
- SQLite (`sqflite`) — offline local storage
- Camera plugin — retinal image capture

**Backend**
- FastAPI — REST API framework
- JWT — API authentication
- Docker — containerized deployment

**Database**
- PostgreSQL — patient and screening records
- SQLite — offline local storage (device-side)

**Dashboard**
- React.js — camp/clinic-level web dashboard
- Tailwind CSS — UI styling

**Cloud & Infrastructure**
- AWS / GCP (or free-tier equivalent) — cloud hosting
- REST APIs — offline-to-cloud batch sync

**Compliance**
- ABDM (Ayushman Bharat Digital Mission) — record structure compatibility

---

## ✅ Feasibility

- Prototype cost under ₹8,000 — affordable, demo-ready build.
- Off-the-shelf components, easily available in India.
- Software stack (PyTorch, Flutter, FastAPI) — open-source and student-friendly.
- Model trainable on a public dataset (APTOS) within hackathon timeframe.
- Fully working prototype achievable within a 36-hour window (capture + AI inference + display).

## 📈 Viability

- **Deployment:** Pilot in one health camp, scalable to hundreds of patients across districts.
- **Cost:** A single smartphone + lens setup replaces the need for a dedicated fundus camera per site.
- **Adoption:** Minimal training needed for health workers; automatic triage logs drive high acceptance by camp coordinators.
- **Sustainability:** Offline-first design keeps operating costs low, with no dependency on constant connectivity.

---

## ⚠️ Potential Challenges & Risks

- **Model accuracy across diverse cases** — a model trained on one dataset may not generalize perfectly across all eye conditions, lighting, or camera qualities.
- **Image quality in field conditions** — poor lighting, shaky hands, or lens smudges could produce unusable captures.
- **Trust & adoption** — health workers may hesitate to act on an AI result without prior training or clinical backing.
- **Regulatory path** — a screening tool sits in a gray zone; scaling beyond pilot stage may eventually require medical-device clearance.
- **Connectivity gaps at sync** — batch sync could pile up screenings if a camp goes multiple days without signal.

## 🛡 Mitigation Strategies

- Continuously expand and diversify the training dataset with real field-collected images over time.
- Build in an on-capture image-quality check, prompting an automatic retake before analysis runs.
- Position the tool as decision support, not diagnosis — with brief health-worker training and clear on-screen disclaimers.
- Start with NGO/state-pilot partnerships under existing screening programs, deferring full certification until proven at scale.
- Design local storage with enough capacity for multi-day offline batches, syncing automatically the moment signal returns.

---

## 🌍 Impact & Benefits

**Who Benefits**
- Rural diabetic patients with no nearby specialist access
- ASHA/health workers running diabetes screening camps
- NGOs and state health departments running rural outreach
- Ophthalmologists, via smarter, pre-filtered referrals

**Direct Benefits**
- Catches DR before symptoms appear → prevents avoidable blindness
- Screening in minutes, no travel to a specialist required
- Low-cost, smartphone-based → no expensive equipment needed
- Works fully offline → built for real rural connectivity
- Explainable results → builds health-worker trust in the AI

## 🇮🇳 Alignment with National Missions

- **Ayushman Bharat Digital Mission (ABDM)** — digital health record interoperability
- **Digital India** — AI-driven healthcare access at the last mile
- **National Programme for Control of Blindness** — preventable-blindness reduction goals
- **Sustainable Development Goal 3** — Good Health & Well-being for all

---

## 🏁 Getting Started

> ⚠️ This project is currently in active hackathon prototype development. Setup instructions will be updated as components are finalized.

```bash
# Clone the repository
git clone https://github.com/xokingvk/retinai.git
cd retinai

# Backend setup (FastAPI)
cd backend
pip install -r requirements.txt
uvicorn main:app --reload

# Mobile app setup (Flutter)
cd ../mobile
flutter pub get
flutter run

# Model training (optional — for retraining)
cd ../model
pip install -r requirements.txt
python train.py
```

---

## 📁 Project Structure

```
retinai/
├── mobile/          # Flutter mobile app
├── backend/         # FastAPI backend + REST APIs
├── model/           # PyTorch training scripts, Grad-CAM integration
├── dashboard/       # React.js coordinator dashboard
├── docs/            # Research papers, references, flowcharts
└── README.md
```

---

## 👥 Team

| Role | Name |
|---|---|
| **Team Leader** | Kamaleshwaran B |
| Team Member | Vishnuvardhan B |
| Team Member | Poojasri AB |
| Team Member | John Ezra P |
| Team Member | Kevin Cris F |
| Team Member | Harini S |

Built for **UCEK Internal Hackathon — Smart India Hackathon 2026** (Problem Statement SIH26038).

---

## 📄 License

This project is licensed under the **Apache License 2.0** — see the [LICENSE](LICENSE) file for details.

```
Copyright 2026 RetinAI Team

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

---

*"AI that shows its work earns the trust a black box never will."*
