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

### 1. Log Exploration

* Used Kibana Discover to inspect logs
* Key fields:

  * `Source_ip`
  * `UserName`
  * `source_state`
  * `@timestamp`

### 2. Filtering & Querying

```kql
Source_ip: "238.163.231.224"
```

```kql
UserName: "Suleman" OR "Rafique M"
```

```kql
NOT source_state : *
```

### 3. Correlation Analysis

* IP ↔ Users
* IP ↔ Locations
* Activity ↔ Time

### 4. Visualization

* User activity over time
* Location-based access
* Detection of spikes/anomalies

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
