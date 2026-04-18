# ELK SIEM Investigation: Suspicious Login Analysis

## Project Overview

This project demonstrates a **SIEM investigation** using the **ELK Stack (Elasticsearch, Logstash, Kibana)**.

The objective was to analyze VPN authentication logs, identify anomalous login behavior, and perform a structured investigation similar to a **SOC analyst workflow**.

---

## Objective

* Detect suspicious login activity
* Correlate multiple data sources (IP, user, location, time)
* Identify potential misuse:

  * VPN/proxy usage
  * Credential sharing
  * Anomalous access patterns

---

## Tools & Technologies

* Elasticsearch
* Kibana (Discover, Lens, Dashboard)
* KQL (Kibana Query Language)
* TryHackMe SIEM Lab

---

## Investigation Methodology

This investigation followed a structured SOC-style workflow to identify and validate suspicious login behavior.

---

### 1️. Log Exploration (Initial Triage)

* Used **Kibana Discover** to analyze raw VPN authentication logs
* Reviewed key fields:

  * `Source_ip`
  * `UserName`
  * `source_state`
  * `@timestamp`
* Observed unusual patterns such as repeated IP usage and missing location data

---

### 2️. Filtering & Querying

Applied **KQL (Kibana Query Language)** to isolate suspicious activity:

```kql
Source_ip: "238.163.231.224"
```

```kql
UserName: "Suleman" OR "Rafique M"
```

```kql
NOT source_state : *
```

* Identified a suspicious IP associated with multiple users
* Detected missing geographic information (possible anonymization)

---

### 3️. Correlation Analysis

Correlated multiple data points to uncover relationships:

* **IP ↔ Users** → Same IP used by multiple accounts
* **IP ↔ Locations** → Activity across different states
* **Activity ↔ Time** → Repeated login patterns

This step confirmed anomalous behavior patterns.

---

### 4️. Visualization & Pattern Analysis

Built visualizations using **Kibana Lens**:

* User activity over time
* Geographic distribution of logins
* Detection of spikes and anomalies

Identified a noticeable increase in login activity in late January.

---

### 5️. Targeted Investigation (User + IP Correlation)

Performed focused analysis using combined filters:

```kql
Source_ip: "238.163.231.224" AND UserName: "Suleman"
```

* Confirmed repeated login activity from the same IP
* Observed consistent behavior patterns
* Strengthened correlation between suspicious entities

---

### 6️. Hypothesis & Validation

Based on findings, the following scenarios were evaluated:

* VPN or proxy usage
* Credential sharing
* Potential unauthorized access

All hypotheses were supported through log correlation and visualization evidence.

---

## Key Findings

### Suspicious IP

**238.163.231.224**

### Users

* Suleman
* Rafique M

### Locations

* Michigan
* New York

---

## Suspicious Indicators

* Same IP used by multiple users
* Same IP across different locations
* Missing `source_state` values
* Spike in activity (late January)

---

## Visual Evidence

### Discover Analysis

![Discover](screenshots/discover.png)

### User Activity Over Time

![User Activity](screenshots/user-activity.png)

### Location Analysis

![Location](screenshots/location-analysis.png)

### Correlation Insight
![Correlation Analysis](screenshots/correlation-analysis.png)

### Targeted Investigation (User + IP Correlation)
![User IP Correlation](screenshots/user-ip-correlation.png)

---

## Security Analysis

The behavior suggests:

* Shared IP usage across accounts
* Multi-location access patterns
* Possible VPN/proxy usage or credential sharing

This is **anomalous and requires monitoring**.

---

## SOC Analyst Perspective

This activity would trigger:

* Medium–High severity alert
* Further investigation:

  * Authentication logs
  * Endpoint activity
  * Network correlation

---

## Project Demo

👉 https://your-video-link-here

---

## Future Improvements

* SIEM alert rules
* Impossible travel detection
* Brute-force detection
* Threat intelligence integration

---

## Skills Demonstrated

* SIEM investigation
* Log correlation
* Threat detection
* Kibana visualization
* KQL querying
* SOC methodology

---

## Author

**Shravan**
Cybersecurity Master's Student – EPITA (Paris, France 🇫🇷)
Aspiring SOC Analyst

Open to Cybersecurity / SOC Internships in Europe
LinkedIn:https://www.linkedin.com/in/shravan-chanda-87280a206/
