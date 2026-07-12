# 🛡️ Project Aegis-AI: Autonomous Cloud SOC Lab

Project **Aegis-AI** is a high-tech Security Operations Center (SOC) laboratory showcasing the future of autonomous defense. It bridges the gap between traditional manual security monitoring and lightning-fast autonomous mitigation by pairing cloud-native SIEM telemetry with advanced Artificial Intelligence reasoning. Developed by **Shaunhacker**.

---

## 🏗️ Architectural Concept

The pipeline functions as an event-driven loop that moves from ingestion to cognitive evaluation, and finally to active remediation:

1. **Ingestion & Detection:** Telemetry flows into **Microsoft Sentinel**, where targeted Kusto Query Language (KQL) rules flag anomalous behavior (e.g., SSH brute-forcing).
2. **Orchestration Brain:** A Python-driven automation hub intercepts the alert payload and extracts the raw, unparsed log strings.
3. **Cognitive Decision Matrix:** Raw telemetry is passed to advanced LLMs (**Gemini Pro / Claude 3.5**). The AI determines if the threat is a True Positive, scores its confidence, and returns a strict JSON-formatted mitigation structure.
4. **Dynamic Enforcement:** If the AI verdict meets your programmatic guardrails (Confidence $\ge 85\%$), the engine hits the Next-Generation Firewall (**NGFW**) API endpoints to block the attacker's IP address instantly.

---

## 🛠️ Lab Directory Structure

```text
aegis-ai-autonomous-soc/
├── README.md                 # Main laboratory documentation
├── CONCEPT_PLAN.md           # Deep-dive architectural roadmap
├── requirements.txt          # Python ecosystem dependencies
├── config/
│   └── settings.yaml         # API credentials and target endpoints
├── src/
│   ├── log_collector.py      # Telemetry logic handler
│   ├── logic_hub.py          # Master SOAR automation brain
│   └── fw_simulator.py       # Simulated NGFW API block control plane
└── detection_rules/
    └── brute_force_ssh.kql   # Microsoft Sentinel detection script
