# 🛡️ DarkShield — Parametric Income Protection for Dark Store Delivery Partners

> **Guidewire DEVTrails 2026 | Phase 1**  
> Persona: Grocery / Q-Commerce (Zepto / Blinkit)

**🌐 Live Demo:** [the-intern-guidewire-b2qv0ve23-nehachinnam956s-projects.vercel.app](https://the-intern-guidewire-b2qv0ve23-nehachinnam956s-projects.vercel.app)  
**🔧 Backend API:** [elegant-love-production.up.railway.app](https://elegant-love-production.up.railway.app)

---

## 📋 Table of Contents

1. [Problem Statement](#problem-statement)
2. [Solution Overview](#solution-overview)
3. [Persona](#persona)
4. [Weekly Premium Model](#weekly-premium-model)
5. [Parametric Triggers](#parametric-triggers)
6. [AI/ML Integration](#aiml-integration)
7. [Adversarial Defense](#adversarial-defense)
8. [Application Workflow](#application-workflow)
9. [Tech Stack](#tech-stack)
10. [Getting Started](#getting-started)
11. [API Reference](#api-reference)

---

## 1. Problem Statement

### The Core Gap We Are Solving

Zepto and Blinkit grocery delivery partners operate on a fundamentally different model from food delivery riders. They work out of **fixed dark stores** — small urban warehouses that serve as the sole pickup point for all their deliveries.

This creates a unique and completely uninsured vulnerability: when a dark store's surrounding zone becomes inaccessible due to an external disruption — flooding, a sudden curfew, a road blockade, or extreme heat — the rider is not just slowed down. **They are completely stranded.**

Unlike food delivery riders who can reroute or switch zones, a Zepto/Blinkit rider has no alternative. Their income is **100% dependent on one fixed geographic point**. No existing insurance product recognises this dark-store dependency as a distinct, insurable risk.

### The Human Story

> *Priya is a Blinkit delivery partner in Bengaluru. She operates out of the Koramangala dark store and delivers groceries within a 3km radius. On a normal day she completes 25–30 deliveries earning ₹850. One Tuesday evening, the storm drain outside her dark store overflows. The entire block is waterlogged. Priya cannot pick up a single order. She earns ₹0 that evening with no recourse.*

**DarkShield is built for Priya.**

---

## 2. Solution Overview

DarkShield is an **AI-powered parametric income protection platform** built exclusively for Zepto and Blinkit grocery delivery partners. It is the first insurance product that treats the **dark store — not the city, not the zone** — as the fundamental unit of risk assessment and claim triggering.

### What Makes DarkShield Genuinely Different

| Feature | Traditional Insurance | DarkShield |
|---|---|---|
| Risk Unit | City / Zone | Individual Dark Store GPS Pin |
| Claim Process | Manual, days/weeks | Automated, minutes |
| Trigger Basis | Self-reported incidents | Multi-source AI validation |
| Payout | Lump sum, delayed | Precise income-proportional, instant UPI |
| Fraud Defense | Basic | GPS + Behavioural + Network graph analysis |

---

## 3. Persona — Grocery / Q-Commerce Delivery Partner

### Who We Are Building For

| Attribute | Details |
|---|---|
| **Platform** | Zepto and Blinkit (primary), Swiggy Instamart (secondary) |
| **Geography** | Tier 1 cities — Bengaluru, Mumbai, Hyderabad, Delhi, Pune |
| **Work Model** | Fixed dark store pickup → hyperlocal 3–5km delivery radius |
| **Daily Earnings** | ₹600 – ₹1,000 (25–35 deliveries/day) |
| **Weekly Earnings** | ₹4,000 – ₹6,500 |
| **Shift Pattern** | Split shifts — morning (8AM–1PM) and evening (5PM–10PM) |
| **Key Vulnerability** | 100% income dependency on a single fixed dark store location |

### Persona-Based Scenarios

**Scenario A — Hyperlocal Flash Flood**  
Priya's Koramangala dark store sits in a low-lying area. A 45-minute cloudburst sends 60mm of rain. DarkShield detects rainfall >40mm at the store's GPS coordinates, cross-checks that platform order volume dropped >70%, and automatically initiates a claim — before Priya even opens the app.

**Scenario B — Sudden Zone Curfew**  
A local protest blocks the 3 roads leading to Arjun's Andheri dark store. DarkShield's social disruption monitor detects the curfew via news API + traffic anomaly data, validates Arjun's location relative to the store, and initiates payout within minutes.

**Scenario C — Extreme Heat Shutdown**  
During a Delhi heatwave (47°C), Zepto suspends deliveries from 11AM–4PM for rider safety. DarkShield detects the platform-level suspension via mock API + IMD heat alert and automatically pays Vikram's afternoon income baseline.

---

## 4. Weekly Premium Model

All premiums are structured on a **weekly basis**, aligned with Zepto/Blinkit's weekly payout cycle. Riders activate or renew coverage every Monday. No annual commitments. Cancel anytime.

### Premium Formula

```
Weekly Premium = Base Rate × Dark Store Risk Score × Shift Exposure Multiplier × Tenure Discount
```

### Sample Weekly Premiums

| Scenario | Calculation | Weekly Premium |
|---|---|---|
| Low-risk store, morning shift, 6-month rider | ₹18 × 0.75 × 1.0 × 0.85 | **₹11/week** |
| Medium-risk store, evening shift, new rider | ₹24 × 1.2 × 1.3 × 1.0 | **₹37/week** |
| High-risk flood-prone store, evening shift | ₹30 × 1.7 × 1.4 × 1.0 | **₹71/week** |

---

## 5. Parametric Triggers

DarkShield uses automated triggers anchored to each rider's specific dark store GPS coordinates — not broad city or zone-level data. All triggers are cross-validated across **at least 2 independent data sources** before a claim is initiated.

### Payout Calculation

```
Payout = Rider Daily Baseline × Disruption Severity % × (Hours Affected / Shift Hours)
```

- **Rider Daily Baseline:** Rolling 28-day average, weighted 1.5x for same day-of-week
- **Disruption Severity:** Determined by trigger threshold breach magnitude
- **Hours Affected:** Real-time monitored, capped at full shift length

**Example:** Priya's daily baseline ₹850. Flash flood blocks her store for 3 hours (of her 5-hour evening shift). Severity = 80%.
```
Payout = ₹850 × 0.80 × (3/5) = ₹408 sent to UPI instantly
```

---

## 6. AI/ML Integration

### Module 1 — Dark Store Risk Scoring Engine
- **Model:** Gradient Boosted Regression (XGBoost)
- **Inputs:** Store GPS coordinates, historical flood/rain/heat data, proximity to water bodies, elevation data, historical claim frequency
- **Output:** Dark Store Risk Score (0.7 – 1.8x multiplier) updated weekly
- **Why unique:** Risk assessed at store-pin level, not city or zone

### Module 2 — Dynamic Premium Calculator
- **Model:** Random Forest Regression
- **Inputs:** Dark store risk score, rider shift pattern, upcoming week weather forecast, rider tenure, city-level disruption calendar
- **Output:** Personalised weekly premium per rider

### Module 3 — Claim Trigger Validator
- **Model:** Multi-source anomaly detection
- **Logic:** Claim fires only when ≥2 independent data sources confirm disruption at store coordinates
- Prevents false positives from single API failures or data glitches

### Module 4 — Fraud Detection
- **GPS trajectory analysis:** Rider should originate from dark store — deviation flagged
- **Order completion cross-check:** If platform shows rider completed deliveries during claimed disruption, auto-reject
- **Cluster fraud detection:** >5 riders from same store claiming same event triggers manual review
- **Historical pattern scoring:** Riders with claim rates >3x store average get enhanced verification

---

## 7. Adversarial Defense & Anti-Spoofing Strategy

> ⚠️ **CRITICAL SECURITY ARCHITECTURE** — Added in response to GPS spoofing syndicate threat

A coordinated syndicate of 500 riders was found using GPS spoofing apps to fake their location inside disruption zones while safely at home, draining insurance liquidity pools. DarkShield's dark-store-centric architecture provides a structural advantage against this attack.

### Genuine Stranding Score (GSS)

Our AI model fuses **5 signals** into a Genuine Stranding Score (0–100):

| Score Range | Action |
|---|---|
| > 70 | Auto-approved, instant payout |
| 40 – 70 | Fast-track manual review (< 2 minutes) |
| < 40 | Auto-rejected, rider asked for simple verification |

### Data Points Collected

**Device-Level Signals (via app SDK)**
- Accelerometer & gyroscope — confirms physical movement consistent with riding
- Cell tower triangulation — validates true location independent of GPS
- Wi-Fi network scan — home Wi-Fi presence during claimed outdoor stranding is a red flag
- Battery consumption pattern — active riding drains battery faster than idle spoofing

**Platform Behavioural Signals (via mock API)**
- Did the rider attempt to accept orders during the disruption window?
- What was the rider's last confirmed delivery completion timestamp and location?

**Environmental Cross-Validation**
- Weather data confirmed at store PIN level from ≥2 independent APIs
- Traffic blockage confirmed via Google Maps API anomaly detection (mock)
- At least 3 other riders from same store must show consistent disruption signals

**Coordinated Ring Detection**
- Network graph analysis for shared device IDs, referral chains, or overlapping claim timestamps
- Velocity check: Rider claiming for the first time on first eligible disruption gets enhanced review

### UX Balance: Protecting Honest Riders

> Key Principle: **We never silently reject.** Every flagged claim gets a human-readable explanation.

- **Network Drop Grace Period:** If a rider's device goes offline during a confirmed disruption (rain killing signal is expected), the claim is held open for 2 hours before scoring
- Honest riders in genuine network-degraded conditions are protected by the 30-minute fast-track review path

---

## 8. Application Workflow

### Step 1 — Onboarding
1. Rider opens DarkShield web app (PWA)
2. Enters Zepto/Blinkit Partner ID and selects their primary dark store from a map
3. System pulls last 28-day earnings history via mock platform API
4. AI risk engine scores the dark store and generates personalised weekly premium
5. Rider pays via UPI — covered from next Monday

### Step 2 — Weekly Policy
- Policy auto-renews every Monday with recalculated premium
- Rider receives: *"Your dark store risk this week: Medium. Premium: ₹34. Coverage: up to ₹4,200 income protection."*
- Rider can pause coverage for vacation weeks with 1-tap

### Step 3 — Disruption Detection & Auto-Claim
- System monitors 5 data feeds continuously at each registered dark store's GPS pin
- Trigger threshold crossed → system checks rider's Genuine Stranding Score
- Automated action taken based on GSS score

### Step 4 — Payout
- Approved claim → payout calculated based on hours affected and daily baseline
- Funds transferred via Razorpay (test mode) / UPI Simulator
- Rider receives: *"DarkShield paid you ₹408 for 3 hours lost to flooding at Koramangala store."*

### Step 5 — Dashboard
- **Rider view:** Weekly earnings protected, active coverage, claim history, store risk level
- **Admin/insurer view:** Store-wise loss ratios, fraud alert queue, weekly disruption forecast, premium adequacy

---

## 9. Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React.js, React Router, Recharts, Leaflet Maps |
| **Backend** | Node.js, Express.js |
| **Database** | SQLite (via sql.js) |
| **Authentication** | JWT, OTP via Twilio |
| **Payments** | Razorpay (test mode) |
| **Deployment — Frontend** | Vercel |
| **Deployment — Backend** | Railway |
| **Platform** | Progressive Web App (PWA) |

---

## 10. Getting Started

### Prerequisites
- Node.js v18+
- npm

### Backend Setup

```bash
# Clone the repo
git clone https://github.com/nehachinnam956/The_intern-guidewire.git
cd The_intern-guidewire

# Install dependencies
npm install

# Create .env file
echo "JWT_SECRET=darkshield_secret" > .env
echo "NODE_TLS_REJECT_UNAUTHORIZED=0" >> .env

# Start the backend
node server.js
```

Backend runs on `http://localhost:5000`

### Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Create .env file
echo "REACT_APP_API_URL=http://localhost:5000/api" > .env

# Start the frontend
npm start
```

Frontend runs on `http://localhost:3000`

---

## 11. API Reference

### Auth
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/send-otp` | Send OTP to phone |
| POST | `/api/auth/verify-otp` | Verify OTP |
| POST | `/api/auth/register` | Register new rider |
| GET | `/api/auth/me` | Get current rider profile |

### Stores
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/stores` | List all dark stores |
| GET | `/api/stores/:id` | Get store by ID |
| POST | `/api/stores/calculate-premium` | Calculate weekly premium |

### Policy
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/policy/create` | Create new policy |
| GET | `/api/policy/active` | Get active policy |
| PATCH | `/api/policy/toggle-pause` | Pause/resume policy |
| PATCH | `/api/policy/cancel` | Cancel policy |

### Claims
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/claims/file` | File a new claim |
| GET | `/api/claims/history` | Get claim history |

### Weather
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/weather/check/:storeId` | Check weather at store |
| GET | `/api/weather/history/:storeId` | Weather history at store |

---

## Dark Stores Covered

| Store ID | Location | City | Risk Score | Risk Label |
|---|---|---|---|---|
| DS001 | Koramangala Hub | Bengaluru | 1.72 | High Flood Risk |
| DS002 | Andheri West Hub | Mumbai | 1.28 | Coastal + Traffic |
| DS003 | Connaught Place | Delhi | 1.15 | Extreme Heat Zone |
| DS004 | Baner Road Hub | Pune | 0.78 | Low Risk Zone |
| DS005 | Hitech City Hub | Hyderabad | 1.02 | Mixed Exposure |

---

*DarkShield — Because Every Dark Store Has a Story Worth Protecting*  
**Guidewire DEVTrails 2026 
