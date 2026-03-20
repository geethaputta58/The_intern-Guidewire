Guidewire DEVTrails 2026
Phase 1 — Idea Document & README
Team: The Intern  |  Persona: Grocery / Q-Commerce (Zepto / Blinkit)

1. Problem Statement
The Core Gap We Are Solving
Zepto and Blinkit grocery delivery partners operate on a fundamentally different model from food delivery riders. They work out of fixed dark stores — small urban warehouses that serve as the sole pickup point for all their deliveries. Every single order begins and ends at one of these locations.

This creates a unique and completely uninsured vulnerability: when a dark store's surrounding zone becomes inaccessible due to an external disruption — flooding, a sudden curfew, a road blockade, or extreme heat — the rider is not just slowed down. They are completely stranded. They cannot pick up a single order. Their income for that entire window drops to zero instantly.

Unlike food delivery riders who can reroute or switch zones, a Zepto/Blinkit rider has no alternative. Their income is 100% dependent on one fixed geographic point. No existing insurance product recognises this dark-store dependency as a distinct, insurable risk.

The Human Story
Priya is a Blinkit delivery partner in Bengaluru. She operates out of the Koramangala dark store and delivers groceries within a 3km radius. On a normal day she completes 25–30 deliveries earning ₹850. One Tuesday evening, the storm drain outside her dark store overflows. The entire block is waterlogged. She cannot enter the store. Orders pile up unassigned. She sits on her bike for 4 hours earning ₹0. No insurance compensates her — because no product was ever designed around the dark store as the unit of risk.

DarkShield is built for Priya.

2. Solution Overview — DarkShield
DarkShield is an AI-powered parametric income protection platform built exclusively for Zepto and Blinkit grocery delivery partners. It is the first insurance product that treats the dark store — not the city, not the zone — as the fundamental unit of risk assessment and claim triggering.

What Makes DarkShield Genuinely Different
Feature	DarkShield Approach
Unit of Risk	The individual dark store, not the city or broad zone
Trigger Logic	Disruption must affect the rider's specific dark store pickup point — not just the general area
Income Baseline	Built from rider's personal delivery completion history at that specific dark store
Fraud Detection	Dark store fixed-origin model makes GPS spoofing uniquely detectable — rider should always start at store
Coverage Scope	Loss of income ONLY — no vehicle, health, or accident coverage

3. Persona — Grocery / Q-Commerce Delivery Partner
Who We Are Building For
•	Platform: Zepto and Blinkit (primary), Swiggy Instamart (secondary)
•	Geography: Tier 1 cities — Bengaluru, Mumbai, Hyderabad, Delhi, Pune
•	Work Model: Fixed dark store pickup → hyperlocal 3–5km delivery radius
•	Typical Daily Earnings: ₹600 – ₹1,000 (25–35 deliveries/day)
•	Typical Weekly Earnings: ₹4,000 – ₹6,500
•	Shift Pattern: Split shifts — morning (8AM–1PM) and evening (5PM–10PM)
•	Key Vulnerability: 100% income dependency on a single fixed dark store location

Persona-Based Scenario
Scenario A — Hyperlocal Flash Flood
Priya's Koramangala dark store sits in a low-lying area. A 45-minute cloudburst sends 60mm of rain. The street floods. Priya cannot enter the store. DarkShield detects rainfall >40mm at the store's GPS coordinates, cross-checks that platform order volume from that store has dropped >70%, and automatically triggers a claim. Payout arrives in her UPI within 3 minutes.

Scenario B — Sudden Zone Curfew
A local protest blocks the 3 roads leading to Arjun's Andheri dark store. Police impose a 2-hour movement restriction. Arjun is stranded 500m away. DarkShield's social disruption monitor detects the curfew via news API + traffic anomaly data, validates Arjun's location relative to the store, and initiates a partial income payout for the blocked hours.

Scenario C — Extreme Heat Shutdown
During a Delhi heatwave (47°C), Zepto suspends deliveries from 11AM–4PM for rider safety. Vikram loses his entire afternoon shift. DarkShield detects the platform-level suspension via mock API + IMD heat alert, confirms it covers Vikram's store zone, and automatically pays his afternoon income baseline.

4. Weekly Premium Model
All premiums are structured on a weekly basis, aligned with Zepto/Blinkit's weekly payout cycle. Riders activate or renew coverage every Monday. No annual commitments. Cancel anytime.

Premium Formula
Weekly Premium  =  Base Rate  ×  Dark Store Risk Score  ×  Shift Exposure Multiplier  ×  Tenure Discount

Component	Range	How Calculated
Base Rate	₹18 – ₹32/week	City-level historical disruption frequency
Dark Store Risk Score	0.7x – 1.8x	Flood/heat/curfew risk score specific to that store's GPS coordinates
Shift Exposure Multiplier	1.0x – 1.4x	Evening shift riders have higher disruption exposure
Tenure Discount	0% – 20%	Loyalty discount for riders with 3+ months of verified history

Sample Weekly Premiums
•	Low-risk store, morning shift, 6-month rider: ₹18 × 0.75 × 1.0 × 0.85 = ₹11/week
•	Medium-risk store, evening shift, new rider: ₹24 × 1.2 × 1.3 × 1.0 = ₹37/week
•	High-risk flood-prone store, evening shift: ₹30 × 1.7 × 1.4 × 1.0 = ₹71/week

5. Parametric Triggers
DarkShield uses automated triggers anchored to each rider's specific dark store GPS coordinates — not broad city or zone-level data. All triggers are cross-validated across at least 2 independent data sources before a claim is initiated.

Trigger	Data Source	Threshold	Payout %
Flash Flood / Heavy Rain	IMD API + OpenWeather + store GPS	>40mm in 90 min at store coordinates	50–100%
Extreme Heat Advisory	IMD heat alert + platform suspension API (mock)	Temp >45°C + platform suspends store zone	75%
Zone Curfew / Strike	News API + Google Traffic anomaly (mock)	Road access to store blocked >60 min	60–100%
Severe Air Pollution	CPCB AQI API	AQI >400 sustained 2+ hrs	50%
Dark Store Forced Closure	Platform operations API (mock)	Platform shuts store due to safety/ops	100%

Payout Calculation
Payout  =  Rider Daily Baseline  ×  Disruption Severity %  ×  (Hours Affected / Shift Hours)

•	Rider Daily Baseline: Rolling 28-day average, weighted 1.5x for same day-of-week
•	Disruption Severity: Determined by trigger threshold breach magnitude
•	Hours Affected: Real-time monitored, capped at full shift length

Example: Priya's daily baseline ₹850. Flash flood blocks her store for 3 hours (of her 5-hour evening shift). Severity = 80%. Payout = ₹850 × 0.80 × (3/5) = ₹408 sent to UPI instantly.

6. AI/ML Integration Plan
Module 1 — Dark Store Risk Scoring Engine
•	Model: Gradient Boosted Regression (XGBoost)
•	Inputs: Store GPS coordinates, historical flood/rain/heat data for that pin, proximity to water bodies, elevation data, historical claim frequency at that store
•	Output: Dark Store Risk Score (0.7 – 1.8x multiplier) updated weekly
•	Why unique: Risk is assessed at store-pin level, not city or zone — far more accurate

Module 2 — Dynamic Premium Calculator
•	Model: Random Forest Regression
•	Inputs: Dark store risk score, rider shift pattern, upcoming week weather forecast, rider tenure, city-level disruption calendar
•	Output: Personalised weekly premium recommendation per rider

Module 3 — Claim Trigger Validator
•	Model: Multi-source anomaly detection
•	Logic: Claim only fires when ≥2 independent data sources confirm the disruption at store coordinates
•	Prevents false positives from single API failures or data glitches

Module 4 — Fraud Detection
•	GPS trajectory analysis: Rider should originate from dark store — deviation flagged
•	Order completion cross-check: If platform shows rider completed deliveries during claimed disruption, auto-reject
•	Cluster fraud detection: >5 riders from same store claiming same event triggers manual review
•	Historical pattern scoring: Riders with claim rates >3x store average get enhanced verification

7. Adversarial Defense & Anti-Spoofing Strategy
⚠️  CRITICAL SECURITY ARCHITECTURE — Added in response to GPS spoofing syndicate threat
A coordinated syndicate of 500 riders was found using GPS spoofing apps to fake their location inside disruption zones while safely at home, draining insurance liquidity pools. DarkShield's dark-store-centric architecture gives us a structural advantage against this attack that food delivery platforms do not have.

7.1 — The Differentiation: Genuine Stranding vs GPS Spoofing
A legitimately stranded Blinkit rider has a very specific, verifiable digital fingerprint that a GPS spoofer cannot easily replicate:

Genuine Stranded Rider	GPS Spoofer at Home
GPS shows movement TO dark store, then stops	GPS appears static inside disruption zone from session start
Device sensors show vibration, acceleration (bike movement)	Accelerometer flat — person is stationary at home
Network switches between cell towers near store	Network tower remains constant — home location
Battery drain pattern consistent with active riding	Battery drain flat — phone idle
Platform app shows login, order queue attempts	Platform app may show no activity if rider forgot to simulate

Our AI model fuses all five signals into a Genuine Stranding Score (0–100). Claims below score 40 are auto-rejected. Claims between 40–70 enter a fast-track manual review queue. Claims above 70 are auto-approved.

7.2 — The Data: Beyond Basic GPS
DarkShield collects and cross-validates the following data points for every claim:

Device-Level Signals (collected via app SDK)
•	Accelerometer & gyroscope data — confirms physical movement consistent with riding
•	Cell tower triangulation — validates true location independent of GPS
•	Wi-Fi network scan — home Wi-Fi presence during claimed outdoor stranding is a red flag
•	Battery consumption pattern — active riding drains battery faster than idle spoofing
•	App foreground/background state — legitimate riders keep the delivery app active

Platform Behavioural Signals (via mock API)
•	Did the rider attempt to accept orders during the disruption window?
•	What was the rider's last confirmed delivery completion timestamp and location?
•	Is the rider's account showing normal login patterns or unusual session behaviour?

Environmental Cross-Validation
•	Weather data must be confirmed at store PIN level from ≥2 independent APIs
•	Traffic blockage confirmed via Google Maps API anomaly detection (mock)
•	At least 3 other riders from the same store must show consistent disruption signals for mass-event claims

Coordinated Ring Detection
•	Network graph analysis: Are claiming riders connected via same device IDs, referral chains, or overlapping claim timestamps?
•	Telegram/social signal proxy: Sudden spike in claims from one store within 10-minute window triggers syndicate alert
•	Velocity check: Rider who has never claimed before suddenly claiming on first eligible disruption gets enhanced review

7.3 — The UX Balance: Protecting Honest Riders
Our biggest design challenge is ensuring that legitimate riders in genuine network-degraded conditions (heavy rain kills cell signal) are not unfairly penalised. Here is how we handle it:

Score	Status	What Happens
70–100	Auto-Approved ✓	Payout sent to UPI within 3 minutes. No friction.
40–69	Fast-Track Review ⚡	Rider gets instant WhatsApp message: 'Claim under quick review. Expected: 30 mins.' Human agent reviews. Honest riders almost always cleared.
20–39	Verification Required 🔍	Rider asked to submit one of: a 10-second video from location, or a photo with dark store in background. Simple for honest rider, hard for spoofer at home.
0–19	Auto-Rejected ✗	Claim denied. Rider notified with specific reason. Can appeal within 48 hours with evidence.

Key Principle: We never silently reject. Every flagged claim gets a human-readable explanation. Honest riders experiencing genuine network drops in bad weather are protected by the 30-minute fast-track review path — not punished by an opaque algorithm.

Network Drop Grace Period: If a rider's device goes offline during a confirmed disruption event (rain killing signal is expected), we hold the claim open for 2 hours before scoring — giving the rider time to reconnect and submit their data.

8. Application Workflow
Step 1 — Onboarding
1.	Rider opens DarkShield web app (PWA)
2.	Enters Zepto/Blinkit Partner ID and selects their primary dark store from a map
3.	System pulls last 28-day earnings and delivery history via mock platform API
4.	AI risk engine scores the dark store and generates personalised weekly premium
5.	Rider reviews coverage and pays via UPI — covered from next Monday

Step 2 — Weekly Policy
6.	Policy auto-renews every Monday with recalculated premium
7.	Rider receives notification: 'Your dark store risk this week: Medium. Premium: ₹34. Coverage: up to ₹4,200 income protection.'
8.	Rider can pause coverage for vacation weeks with 1-tap

Step 3 — Disruption Detection & Auto-Claim
9.	System monitors 5 data feeds continuously at each registered dark store's GPS pin
10.	Trigger threshold crossed → system checks rider's Genuine Stranding Score
11.	Score >70: Auto-claim initiated, rider notified immediately
12.	Score 40–70: Fast-track review triggered, rider notified within 2 minutes
13.	Score <40: Claim flagged, rider asked for simple verification

Step 4 — Payout
14.	Approved claim → payout calculated based on hours affected and daily baseline
15.	Funds transferred via Razorpay (test mode) / UPI Simulator
16.	Rider receives: 'DarkShield paid you ₹408 for 3 hours lost to flooding at Koramangala store.'

Step 5 — Dashboard
17.	Rider view: Weekly earnings protected, active coverage, claim history, store risk level
18.	Insurer/admin view: Store-wise loss ratios, fraud alert queue, weekly disruption forecast, premium adequacy

9. Platform Choice — Progressive Web App (PWA)
•	Zepto/Blinkit riders use Android smartphones — PWA gives native app feel without Play Store friction
•	Works offline — critical when rider is in a disruption zone with degraded connectivity
•	Admin/insurer dashboard naturally suits web interface
•	Faster iteration across all 3 hackathon phases without build/release cycles

10. Tech Stack
Layer	Technology
Frontend	React.js (PWA) + TailwindCSS
Backend	Node.js + Express / FastAPI (Python for ML)
AI / ML	Python: XGBoost, scikit-learn, Pandas, NumPy
Database	PostgreSQL (policies, riders) + Redis (real-time trigger cache)
Weather API	OpenWeatherMap (free tier) + IMD mock data
Anti-Spoofing	Custom device signal SDK (accelerometer, cell tower, Wi-Fi scan)
Payment	Razorpay Test Mode + UPI Simulator
Notifications	WhatsApp Business API (mock) + In-app push
Hosting	Vercel (frontend) + Railway (backend + ML endpoints)

11. Development Plan
Phase	Timeline	Key Deliverables
Phase 1	Mar 4–20	Problem statement, persona research, dark store risk model design, this README, anti-spoofing architecture
Phase 2A	Mar 21–28	Rider onboarding, dark store map selector, mock earnings integration, premium engine v1
Phase 2B	Mar 29–Apr 4	Parametric trigger engine, multi-source validation, auto-claim pipeline, UPI payout
Phase 3A	Apr 5–11	Anti-spoofing SDK, Genuine Stranding Score model, fraud ring detection, fast-track review UX
Phase 3B	Apr 12–17	Analytics dashboard, final integration, 5-min demo video, pitch deck

DarkShield — Because Every Dark Store Has a Story Worth Protecting
Guidewire DEVTrails 2026  |  Phase 1  |  March 20, 2026
