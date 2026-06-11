---
title: "Medical Protocol & Field Safety Architecture"
description: "Real-time telemetry, offline-capable alerts, and verified response protocols for 35-day Taiwan circumnavigation."
summary: "Circuit Taiwan deploys a multi-layer safety system: continuous vital sign monitoring, lightning detection (AS3935), weather API integration, and pre-mapped extraction points. All protocols are field-tested and medically supervised."
date: 2026-06-03
draft: false
tags: ["medical", "safety", "engineering", "telemetry"]
toc: true
---

Circuit Taiwan is not just an expedition—it is a **mobile medical field study**. Over 35 days, we will collect continuous physiological and environmental data while maintaining medically-supervised safety protocols at every kilometer.

This document outlines the operational safety architecture, alert thresholds, and response protocols that protect the expedition leader throughout the journey.

<!--more-->

## Continuous Monitoring Architecture

### Vital Signs Telemetry (Real-Time)

| Parameter | Sensor | Sampling Rate | Alert Threshold | Critical Threshold |
|-----------|--------|---------------|-----------------|-------------------|
| **Heart Rate** | Polar H10 chest strap | 1 Hz (every second) | <45 or >160 bpm | <35 or >180 bpm |
| **SpO₂ (Blood Oxygen)** | Nonin pulse oximeter | Every 15 sec | <92% | <88% |
| **Core Temperature** | ingestible thermometer pill | Every 5 min | >38.5°C | >39.5°C |
| **Skin Temperature** | iButton sensors (4 locations) | Every 1 min | >37°C or <32°C | >38°C or <30°C |
| **Battery Voltage** | Wheelchair telemetry | Every 30 sec | <20% capacity | <10% capacity |
| **Wheelchair Motor Temp** | Thermal sensors | Every 1 min | >65°C | >75°C |

### Environmental Monitoring

| Parameter | Sensor | Alert Threshold | Response |
|-----------|--------|-----------------|----------|
| **Lightning Detection** | AS3935 Franklin sensor | Strike within 15 km | Immediate shelter protocol |
| **Ambient Temperature** | DHT22 sensor | >33°C with humidity >80% | Cooling break required |
| **Wind Speed** | Anemometer | >40 km/h sustained | Route reassessment |
| **UV Index** | VEML6075 sensor | >8 (Very High) | SPF reapplication + shade |

## Multi-Layer Alert System

### Level 1: Advisory (Yellow)
**Trigger:** Single parameter outside normal range for >5 minutes

**Examples:**
- Heart rate 155-160 bpm sustained
- SpO₂ 90-92%
- Battery 20-25%

**Response:**
- Audible alert to expedition leader
- Writer notified via smartwatch
- Increase monitoring frequency to every 30 seconds
- Log event in field journal

### Level 2: Warning (Orange)
**Trigger:** Two parameters abnormal OR one parameter in critical zone

**Examples:**
- Heart rate >160 bpm + core temp >38.5°C
- Lightning detected within 15 km
- Battery <15%

**Response:**
- Immediate stop required
- Driver activates extraction protocol
- Medical advisor contacted via satellite messenger
- Vital signs transmitted every 10 seconds
- Nearest shelter/hospital identified on map

### Level 3: Emergency (Red)
**Trigger:** Life-threatening parameter OR loss of communication

**Examples:**
- Heart rate >180 bpm or <35 bpm
- SpO₂ <88% for >2 minutes
- Core temp >39.5°C
- No telemetry signal for >3 minutes

**Response:**
- Automatic GPS coordinates sent to medical advisor
- Driver initiates emergency extraction to pre-mapped hospital
- Satellite SOS activated if no response in 5 minutes
- Emergency contacts notified automatically

## Pre-Mapped Extraction Points

### East Coast (Su-Hua Highway Segment)

| KM Marker | Location | Nearest Hospital | Distance | ETA by Van |
|-----------|----------|------------------|----------|------------|
| **KM 112** | Chongde Rest Area | Hualien Tzu Chi Hospital | 28 km | 35 min |
| **KM 145** | Xincheng Township | Hualien General Hospital | 15 km | 22 min |
| **KM 178** | Nan'ao Village | Nan'ao Clinic (stabilization only) | 2 km | 5 min |
| | → Transfer to | Su-Ao Veterans Hospital | 18 km | 25 min |
| **KM 201** | Dong'ao Station | Su-Ao Veterans Hospital | 12 km | 18 min |
| **KM 234** | Heping Industrial Zone | Hualien Tzu Chi Hospital | 45 km | 55 min |

### West Coast (Urban Segment)

| KM Marker | Location | Nearest Hospital | Distance | ETA by Van |
|-----------|----------|------------------|----------|------------|
| **KM 45** | Kaohsiung City Center | Kaohsiung Medical University Hospital | 3 km | 8 min |
| **KM 89** | Tainan City | National Cheng Kung University Hospital | 5 km | 12 min |
| **KM 134** | Chiayi City | Chang Gung Memorial Hospital | 8 km | 15 min |
| **KM 178** | Yunlin County | Changhua Christian Hospital | 22 km | 28 min |

## Medical Supervision Structure

### On-Call Medical Advisor
- **Role:** Remote monitoring and decision support
- **Availability:** 06:00-22:00 daily (Taiwan time)
- **Communication:** Satellite messenger + WhatsApp + phone
- **Credentials:** Emergency medicine specialist with expedition experience

### Local Emergency Contacts
- **119:** Taiwan emergency services (ambulance/fire)
- **112:** Universal emergency number (works without SIM)
- **Hospital hotlines:** Pre-programmed for each extraction zone

### Equipment Inventory

| Item | Quantity | Location |
|------|----------|----------|
| Automated External Defibrillator (AED) | 1 | Support van |
| Emergency medication kit | 1 | Wheelchair + van |
| Portable oxygen concentrator | 1 | Wheelchair |
| Backup battery packs (12V) | 4 | Van (2) + Wheelchair (2) |
| Satellite messenger (Garmin inReach) | 2 | Leader + Driver |
| First aid kit (wilderness-rated) | 2 | Van + Wheelchair |

## Data Collection & Privacy

### What We Collect
- Continuous vital signs (HR, SpO₂, temperature)
- GPS location and speed
- Environmental conditions (weather, air quality)
- Equipment performance metrics
- Subjective wellness scores (self-reported every 4 hours)

### How We Use It
- **Real-time:** Safety monitoring and alert triggering
- **Post-expedition:** Medical research publication (anonymized)
- **Open-source:** Aggregated accessibility and safety data released under Creative Commons

### Privacy Protection
- All personal health data encrypted at rest and in transit
- Public datasets anonymized (no individual identifiers)
- Medical advisor bound by confidentiality agreement
- Data retention: 5 years post-expedition, then secure deletion

## Field Testing Results (Pilot Phase)

### Test Run: Taipei to Yilan (March 2026)
- **Distance:** 95 km
- **Duration:** 11 hours
- **Alerts triggered:** 3 (all Level 1 - advisory)
  - Heart rate spike to 158 bpm (uphill segment)
  - Battery warning at 22% (resolved with solar charging)
  - Lightning alert at 18 km distance (shelter protocol activated)

**Outcome:** All systems functional. Response times within acceptable parameters. Protocol refinements implemented.

### Test Run: Kaohsiung to Tainan (April 2026)
- **Distance:** 48 km
- **Duration:** 5.5 hours
- **Environmental conditions:** 34°C ambient, 85% humidity
- **Alerts triggered:** 2 (Level 2 - warning)
  - Core temperature reached 38.7°C (cooling break initiated)
  - SpO₂ dropped to 91% for 3 minutes (rest + oxygen)

**Outcome:** Heat stress protocol validated. Additional cooling measures added to standard equipment.

---

*This protocol is a living document. Updates are published as field testing reveals optimization opportunities. Last updated: June 2026.*

*Questions about medical partnerships or safety architecture? Contact: rollfree142@gmail.com*