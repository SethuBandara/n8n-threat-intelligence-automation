# n8n Threat Intelligence Automation

A hands-on cybersecurity automation project developed to explore **workflow orchestration, threat intelligence integration, and automated security notifications** using n8n.

## Overview

This project implements a simple automated IP security-checking workflow. An IP address is submitted through an n8n Webhook, analyzed using the **VirusTotal API**, processed using JavaScript-based logic, and the resulting security status is delivered through **Telegram**.

## Workflow Architecture

```text
IP Address
    │
    ▼
Webhook
    │
    ▼
Input Processing
    │
    ▼
VirusTotal API
    │
    ▼
JavaScript Risk Analysis
    │
    ▼
Conditional Evaluation
    │
    ▼
Telegram Notification
```

## Technologies

* **n8n** — Workflow automation and orchestration
* **VirusTotal API** — IP threat-intelligence analysis
* **JavaScript** — Data processing and risk calculation
* **REST API / Webhooks** — Event and data exchange
* **Telegram** — Automated security notifications
* **PowerShell** — Webhook testing

## Implementation

### 1. Webhook-Based Input

The workflow accepts an IP address through an HTTP POST request.

```json
{
  "ip": "8.8.8.8"
}
```

### 2. Threat Intelligence Lookup

The submitted IP is queried against the VirusTotal API to retrieve available analysis statistics, including:

* Malicious detections
* Suspicious detections

### 3. Risk Analysis

A JavaScript Code node calculates a simplified risk score:

```text
Risk Score = (Malicious × 5) + (Suspicious × 2)
```

The score is capped at 100 and mapped to a basic severity level:

| Risk Score | Severity |
| ---------: | -------- |
|       0–29 | LOW      |
|      30–69 | MEDIUM   |
|     70–100 | HIGH     |

> **Note:** The scoring model is a custom heuristic created for learning purposes and is not an official VirusTotal severity rating.

### 4. Automated Notification

The processed result is sent to Telegram based on the workflow's conditional evaluation.

### Example Output

```text
✅ IP SECURITY CHECK

IP: 8.8.8.8

Malicious detections: 0
Suspicious detections: 0

Risk Score: 0/100
Severity: LOW

Status: No significant malicious activity detected.
```

## Key Learning Outcomes

This project provided practical experience with:

* Cybersecurity workflow automation
* Threat intelligence API integration
* Webhook-based event processing
* REST API communication
* JSON data handling
* JavaScript within n8n
* Conditional workflow logic
* Automated security notifications
* PowerShell-based API testing

## Security Considerations

No API keys, bot tokens, or other sensitive credentials are stored in this repository.

When deploying similar workflows, credentials should be managed securely using the platform's credential-management mechanisms rather than hard-coded into workflow logic.

## Future Enhancements

Potential extensions include:

* Security event logging
* Additional threat-intelligence sources
* Email-based alerts
* SIEM integration
* Automated incident tracking
* More robust risk-scoring methodology

## Author

**Sesadi Bandara**
BSc in Information & Communication Technology
**Specialization: Network and Security Technologies**

Areas of Interest: **Cybersecurity • Network Security • Threat Intelligence • SOC Operations • Security Automation**

---

### Disclaimer

This project was developed for **educational and authorized security-testing purposes**. The risk-scoring mechanism is a simplified learning implementation and should not be used as a standalone security decision-making system.
