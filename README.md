

# OR-1: Multimodal Neural-Metabolic Surgical Monitor

An advanced, fault-tolerant edge-computing framework designed to reduce "alert fatigue" and lower a surgeon's cognitive load during high-stress procedures. By utilizing a **Generalized Linear Model (GLM)** framework, the system intelligently fuses multi-channel electroencephalogram (EEG) neural data with electrocardiogram (EKG) metabolic metrics to dynamically evaluate patient distress.

---

## Core Architecture & Features

### 1. Multimodal Sensor Fusion (GLM Framework)

The system leverages a deterministic Generalized Linear Model to decode patient states in real time. It compresses multi-channel biological streams into localized features and applies an optimized linear weight matrix to calculate a unified patient distress metric:

$$fused\_score = (\text{Neural Score} \times 0.6) + (\text{Vitals Score} \times 0.4)$$

This score is passed through an adaptive, non-linear threshold gate to accurately classify the patient's state as `STABLE` or `ALARM`.

### 2. Intelligent Noise Mitigation & "Social Grace"

Medical theaters are chaotic environments filled with electrical noise. OR-1 mitigates false positives through:

* **High-Frequency Rejection:** Detecting and isolating electrical interference (e.g., 60Hz hum or Bovie cauterizer tool activation).
* **Temporal Smoothing:** Differentiating sudden, temporary surgical "startle responses" from sustained biological distress.

### 3. Reinforcement Learning via Vocal Overrides

To respect the surgeon's operational focus, the system incorporates a "Human-in-the-Loop" feedback mechanism. Using direct vocal confirmations (`"CONFIRMED"` / `"UNSTABLE"`), the system applies a dynamic bias adjustment ($\pm5$) to shift the alarm trigger threshold dynamically, tailoring its sensitivity to the specific patient baseline and surgeon preference.

### 4. High-Reliability Resilience & "Limp-Home" Protocols

Engineered for critical care, the system treats biological stillness not as stability, but as a potential technical failure.

* **Hardware Detachment Check:** Flags raw signal loss ($\sum X = 0$).
* **Software Freeze Detection:** Identifies system lockups by tracking micro-variances ($\sigma = 0.0$).
* **Graceful Degradation:** Instantly shifts weights to $w_{neural}=0.0$ and $w_{vitals}=1.0$ if a sensor dies, keeping the surgeon informed via secondary channels rather than crashing.

### 5. Ethical Escalation Framework

To manage high-stakes scenarios where a fixated operator might dismiss a critical event, the architecture implements an **Escalation Hierarchy**. High-confidence alarms ($>90\%$) that face localized dismissal are automatically rerouted as a secondary notification to adjacent surgical staff (e.g., the Anesthesiologist), establishing robust Distributed Situational Awareness.

---

## Tech Stack & Methods

* **Language:** Python 3.x
* **Libraries:** NumPy (Vectorized Signal Processing, Matrix Math)
* **Concepts applied:** Generalized Linear Models (GLMs), Reinforcement Learning (Policy/Bias Updating), Fault-Tolerant System Design, High-Reliability Organizing (HRO).

---

## Future Extensions: Representational Similarity Analysis (RSA)

* **Current Iteration:** Linear weighted-sum decoder optimized for ultra-low latency edge deployment.
* **Next Phase:** Integration of a real-time **Representational Similarity Analysis (RSA)** engine. By utilizing a correlation distance metric ($1 - r$) to construct Representational Dissimilarity Matrices (RDMs), the next generation will compare multi-channel spatial geometry against pre-recorded reference states (e.g., deep anesthesia vs. nociceptive shock) to transition from threshold alerting to geometric brain-state classification.
