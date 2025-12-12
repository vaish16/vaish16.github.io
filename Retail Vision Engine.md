# Retail Vision Engine — Technical Overview

## TL;DR
Retail Vision Engine is a multimodal AI system built with **Gemini 2.5** to extract structured retail insights from shelf images. The system currently runs backend-based inference (v1) and is evolving toward real-time AI responses (v2), with a roadmap that includes price detection, out-of-stock detection, and task routing through chaining.

---

## 1. Project Overview
Retail Vision Engine is a multimodal AI system designed to automatically extract structured retail insights from in-store shelf images. The system converts raw images captured during retail surveys into machine-readable product and pricing data, reducing manual entry and enabling scalable analytics workflows.

The architecture is intentionally extensible, allowing new vision-based retail tasks to be added incrementally without reworking the core pipeline.

---

## 2. Core Capabilities (Current)
- Image-based extraction of **product identifiers and pricing information**
- Prompt-engineered multimodal reasoning using **Gemini 2.5**
- Deterministic, structured JSON outputs
- Seamless integration with survey, backend, and analytics systems

---

## 3. Architecture Overview

### v1 — Backend Inference (Live)
- Retail images captured through a survey application
- Images sent to backend services
- Backend invokes **Gemini 2.5** using task-specific prompts
- Model responses parsed into structured fields (products, prices)
- Outputs persisted and surfaced through analytics dashboards

**Characteristics:**
- Centralized AI orchestration
- Easier observability and iteration
- Stable latency and controlled execution environment

---

### v2 — Real-Time Inference (In Progress)
- Moves AI inference closer to the user interaction layer
- Enables AI responses during the survey workflow
- Provides immediate validation and feedback to survey takers

**Design goals:**
- Reduced end-to-end latency
- Improved data quality at capture time
- Minimized post-survey correction workflows

---

## 4. Model & Prompt Design
- Leverages **Gemini 2.5 multimodal reasoning**
- Prompts designed to:
  - Focus on retail shelf context
  - Distinguish pricing labels from visual noise
  - Produce consistent, structured outputs
- Prompt logic is modular to support future task specialization

---

## 5. Data Flow & Integration
- Clearly defined input/output schemas between frontend, backend, and analytics layers
- JSON-based contracts to ensure compatibility across systems
- Designed for:
  - Backward compatibility across versions
  - Incremental schema expansion
  - Minimal refactoring as new tasks are added

---

## 6. Versioning Strategy
- **v1:** Backend-based inference, currently live
- **v2:** Real-time inference architecture under implementation
- Shared prompt logic and output contracts across versions

---

## 7. Roadmap & Future Extensions

### Planned Capability Branches
- **Price Detection:** Accuracy improvements and edge-case handling
- **Out-of-Stock Detection:** Visual inference for missing or unavailable SKUs
- **Promotion Detection:** Differentiating promotional tags from regular pricing

### Chaining & Routing
- Task-based routing to select appropriate prompts or models
- Multi-step reasoning chains for complex shelf scenarios
- Modular expansion without rewriting core inference logic

---

## 8. Design Philosophy
- MVP-first, extensible architecture
- Separation of inference, orchestration, and presentation layers
- Model-agnostic design to support future upgrades
- Focus on reliability, scalability, and real-world usability

---

## 9. Current Status
- **v1:** Deployed and operational
- **v2:** Actively under development
- Additional vision tasks planned as incremental extensions
