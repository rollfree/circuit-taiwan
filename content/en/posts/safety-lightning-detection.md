---
title: "Engineering Safety: Why a Wheelchair User Needs Lightning Detection on Taiwan's Coast"
description: "How Circuit Taiwan's integrated, offline-capable safety system uses lightning detection and biometric telemetry to protect a vulnerable road user on the Su-Hua Highway."
summary: "When cell service drops in a tunnel and a subtropical storm rolls in, a smartphone weather app is useless. Here is how we are building an offline, multi-layered early warning system to keep the expedition safe."
date: 2026-06-19
draft: false
tags: ["safety", "engineering", "lightning-detection", "su-hua-highway", "technology"]
toc: true
---

Twenty-five years ago, I drove the Su-Hua Highway in a car. When a storm approached, I turned on the wipers, maybe slowed down, and kept driving. I had a metal roof, air conditioning, and the ability to accelerate out of trouble.

In September 2027, I will attempt the same route in an electric wheelchair.

The difference in vulnerability is massive. A wheelchair user is low to the ground, physically exposed to the elements, and moves at a fraction of the speed of motorized traffic. When a subtropical thunderstorm rolls in over the Pacific, "getting to shelter" isn't a matter of speeding up. It is a matter of knowing the storm is coming long before the first drop of rain falls.

This is why Circuit 台灣 is building a custom, offline-capable safety and early-warning system.

### The Problem: Dead Zones on the Su-Hua

The Su-Hua Highway Improvement Project (蘇花改), completed in 2021, made the route newly viable for slow, non-motorized travel. But it also created long tunnel sections where cell service disappears. 

Most people rely on smartphone weather apps. But when LTE signal vanishes in a tunnel, your weather radar goes blank. By the time you can physically see the storm, you are already in it. We cannot rely on the cloud. We need ground truth.

### The Solution: Multi-Layered, Offline Safety

Our integrated safety system operates entirely independently of internet or mobile networks. It relies on three layers of local data:

**1. Local Ground Truth (The Hardware)**
We are integrating a dedicated **lightning detection unit** capable of sensing strikes up to 40 km away, paired with a **compact weather station** measuring atmospheric pressure, temperature, and humidity. 
*   *The logic:* A rapid drop in barometric pressure is the most reliable physical indicator of an approaching storm cell. If the pressure drops and the lightning detector pings, we have physical proof of danger, regardless of cell service.

**2. Biometric Feedback (The Body)**
A medical-grade smartwatch will continuously monitor heart rate, Heart Rate Variability (HRV), blood oxygen (SpO2), and skin temperature. 
*   *The logic:* In 35°C heat and 90% humidity, physical fatigue and heat stress can impair decision-making before the brain consciously registers it. The watch acts as an early warning system for the rider’s physical limits.

**3. The AI Co-Pilot (The Brain)**
This is where the hardware meets intelligence. All this data is fed into an edge-computing AI module mounted directly on the wheelchair. 
*   *The logic:* The AI calculates the intersection probability of the storm cell against our current speed and heading. It doesn't just say "storm nearby." It calculates *when* the storm will intersect with our exact position, giving the team precise time to execute an extraction.

### The Alert Protocol

Data is useless if it doesn't reach the human. When riding, wind noise, tunnel echoes, and rain on a helmet can mask audio alarms. Therefore, the alert system is multi-sensory:

*   **CLEAR:** Normal operation.
*   **WATCH:** Soft vibration in the seat cushion and a visual cue on the smartwatch. The team begins identifying the nearest shelter.
*   **WARNING:** Continuous vibration, audio alarm, and voice prompt. The assistance vehicle moves into position.
*   **DANGER:** Maximum alarm. SEEK SHELTER NOW. The vehicle opens its doors immediately. The rider is loaded into the van within seconds.
*   **TYPHOON:** Full expedition pause. No resumption until the Central Weather Administration (CWA) issues an all-clear.

### Honest Limitations

We are testing smart glasses with a heads-up display for visual alerts. However, in the blinding direct sunlight of the Taiwan coast, a visual overlay is incredibly difficult to read. The physical vibration in the seat and the smartwatch on the wrist remain our most reliable fail-safes. The technology must serve the reality of the environment, not the other way around.

### The Ultimate Goal: Open-Source Safety

This system is being built to keep me safe on the Su-Hua Highway in 2027. But the ultimate goal is much larger.

At the end of the expedition, the engineering design, the sensor fusion logs, the offline inference benchmarks, and the safety protocols will be published as an **open-source safety framework**. 

We want to prove that with modern edge-computing and localized sensors, we can create a safety net for vulnerable road users—whether they are in a wheelchair, on a bicycle, or walking—that doesn't require a cell signal to keep them alive.

---

*Read this post in [繁體中文](/zh/posts/safety-lightning-detection/) or [Français](/fr/posts/safety-lightning-detection/).*