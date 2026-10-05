# OpenCTI + Wazuh Threat Intelligence Integration

A threat-intelligence enrichment project that integrates **OpenCTI with Wazuh** to add contextual intelligence to security events detected within a SOC home laboratory.

The project connects Wazuh with **OpenCTI**, **URLhaus**, **AlienVault OTX**, and **MITRE ATT&CK**, using a custom Python integration to query OpenCTI through its GraphQL API. When a monitored security event contains a relevant indicator, the integration queries OpenCTI and returns threat intelligence such as threat score, confidence, labels, malware context, and MITRE ATT&CK information.

The resulting intelligence is processed by custom Wazuh rules and presented as an enriched security alert for analyst investigation.

**Core workflow:**

`Security Event → Wazuh → OpenCTI GraphQL → Indicator Matching → Threat Intelligence Enrichment → Wazuh Alert`


## Project Overview

This project extends an existing **Security Operations Center (SOC) home laboratory** by introducing OpenCTI as a structured cyber threat intelligence platform and integrating it with Wazuh.

The implementation was designed to move beyond isolated security-event detection by allowing observed activity to be compared against external threat intelligence. This enables Wazuh alerts to be enriched with additional context, including malicious indicators, confidence levels, threat scores, labels, malware information, and MITRE ATT&CK data.

The project uses **OpenCTI**, **Wazuh**, **URLhaus**, **AlienVault OTX**, and **MITRE ATT&CK**, with a custom Python integration serving as the bridge between Wazuh and the OpenCTI GraphQL API.

The final implementation demonstrated an end-to-end workflow in which a known malicious URLhaus indicator was detected, queried against OpenCTI, enriched with threat intelligence, and returned to Wazuh as a high-severity alert.


## Scope & Objectives

### Scope

The project focused on integrating **OpenCTI into an existing Wazuh-based SOC home laboratory** to provide structured threat-intelligence enrichment for security events.

The implementation covered:

- Deployment and configuration of OpenCTI using Docker Compose.
- Integration of **URLhaus**, **AlienVault OTX**, and **MITRE ATT&CK**.
- Development of a custom Python-based integration between Wazuh and the OpenCTI GraphQL API.
- Extraction and correlation of indicators such as IP addresses from monitored security events.
- Enrichment of Wazuh alerts with threat scores, confidence levels, labels, malware context, and MITRE ATT&CK information.
- Application of threat intelligence to existing Wazuh detection use cases.
- Testing using Linux `auditd` network connection events and SSH activity.
- End-to-end validation using a known malicious URLhaus indicator.

All technical validation was performed within the controlled laboratory environment or against known threat-intelligence indicators. The project did **not** include penetration testing, exploitation of external systems, unauthorized scanning, or security assessment of third-party organizations.

### Objectives

The main objective was to integrate OpenCTI with Wazuh to enhance security-event detection with structured and contextual threat intelligence.

Specific objectives included:

1. Deploy OpenCTI within the existing SOC laboratory environment.
2. Integrate URLhaus, AlienVault OTX, and MITRE ATT&CK.
3. Develop a custom Wazuh-to-OpenCTI integration using the OpenCTI GraphQL API.
4. Extract and correlate indicators from monitored security events with intelligence stored in OpenCTI.
5. Enrich Wazuh alerts with threat intelligence when an indicator match is identified.
6. Create dedicated Wazuh rules to process enrichment results.
7. Apply threat intelligence enrichment to an existing SOC detection.
8. Validate the complete workflow from security-event generation to the final enriched Wazuh alert.
9. Document implementation challenges and their resolutions.
10. Demonstrate the practical use of OpenCTI for organizational threat intelligence.
