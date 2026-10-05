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

 ## Methodology

The project was implemented in four major stages:

1. **OpenCTI Deployment and Configuration**  
   OpenCTI was deployed within the existing Kali Linux SOC environment using Docker Compose and configured with its required supporting services.

2. **Threat Intelligence Feed Integration**  
   External intelligence sources were connected to OpenCTI, including URLhaus, AlienVault OTX, and MITRE ATT&CK.

3. **Wazuh-to-OpenCTI Enrichment Pipeline**  
   A custom Python integration was developed to receive relevant Wazuh alerts, extract indicators, query OpenCTI through its GraphQL API, and return the resulting threat intelligence to Wazuh.

4. **Application to SOC Detection and Validation**  
   The enrichment workflow was applied to network and SSH-related security events and validated using a known malicious URLhaus indicator.

   
## Architecture & Environment

The project extended the existing SOC laboratory by introducing **OpenCTI as the threat-intelligence layer** alongside the existing Wazuh monitoring infrastructure.

![Final OpenCTI + Wazuh Architecture](screenshots/final-opencti-wazuh-architecture.png)

*Figure: Final architecture of the SOC environment showing the relationship between the network, endpoints, Wazuh, OpenCTI, and external threat-intelligence sources.*

### Architecture Overview

The architecture begins at the **Internet**, where traffic enters the laboratory through the **pfSense firewall**. pfSense provides the network boundary and connects the external network to the internal virtual environment.

Inside the internal network are the laboratory systems used for security monitoring and testing:

- **Kali Linux** — the central system for the project. It hosts the Wazuh Manager, Wazuh Indexer, Wazuh Dashboard, and the Docker-based OpenCTI deployment.
- **Windows 11** — provides Windows endpoint telemetry through the Wazuh Agent and Sysmon and was also used with Atomic Red Team for security-event generation.
- **Ubuntu** — provides Linux endpoint telemetry through the Wazuh Agent.

### Wazuh Layer

Wazuh remains responsible for collecting and processing security telemetry from the monitored endpoints.

Endpoint activity is forwarded to Wazuh, where events are processed by the Wazuh Manager and presented through the Wazuh Dashboard. The project therefore keeps the existing SIEM and detection workflow while adding threat-intelligence enrichment on top of it.

### OpenCTI Layer

OpenCTI was introduced as the central **threat-intelligence platform**.

It runs on Kali through Docker and uses supporting services including **Elasticsearch/OpenSearch, Redis, RabbitMQ, and MinIO**.

OpenCTI provides the platform for storing, organizing, correlating, and querying threat intelligence from external sources.

### External Threat Intelligence

The architecture also shows external threat-intelligence sources feeding information into OpenCTI.

For the implemented project, the primary sources were **URLhaus** and **AlienVault OTX**, with **MITRE ATT&CK** providing structured adversary, malware, and technique relationships.

This allows an indicator observed in a Wazuh security event to be compared with intelligence already available in OpenCTI.

### Wazuh–OpenCTI Integration

The key addition introduced by this project is the connection between **Wazuh and OpenCTI**.

A custom Python integration, `custom-opencti.py`, acts as the bridge. When Wazuh generates a relevant security event, the integration extracts the indicator, queries OpenCTI through its **GraphQL API**, and returns the available threat-intelligence context.

The resulting workflow is:

```text
Security Event
      ↓
    Wazuh
      ↓
Indicator Extraction
      ↓
OpenCTI GraphQL Query
      ↓
Threat Intelligence Match
      ↓
Score / Confidence / Labels / Context
      ↓
Enriched Wazuh Alert
```

This architecture therefore extends the existing SOC monitoring capability without replacing Wazuh. **Wazuh remains responsible for detection and alerting, while OpenCTI provides the intelligence context needed to give those alerts greater investigative value.**

## Phase One — OpenCTI Deployment & Configuration

The first phase focused on deploying and preparing **OpenCTI** within the existing SOC laboratory environment.

Due to available system resources, OpenCTI was deployed directly on the existing **Kali Linux** system using **Docker Compose** rather than creating an additional virtual machine.

### OpenCTI Deployment

OpenCTI was deployed together with its supporting services required for the platform to operate, including:

- Elasticsearch/OpenSearch
- Redis
- RabbitMQ
- MinIO

The deployment provided the foundation for collecting, storing, correlating, and querying threat-intelligence data within the laboratory.

![OpenCTI Docker Deployment](screenshots/ACTUAL-DOCKER-DEPLOYMENT.png)

*Figure: Docker deployment.*

### Initial OpenCTI Configuration

After deployment, OpenCTI was configured as the central threat-intelligence platform for the integration project.

The **MITRE ATT&CK** intelligence source was enabled during this phase to provide structured information about adversaries, malware, and attack techniques.

This established the initial intelligence layer that would later be combined with additional external sources such as **URLhaus** and **AlienVault OTX**.

### Phase One Outcome

At the end of this phase, OpenCTI was deployed and configured as the threat-intelligence platform that would support the subsequent Wazuh integration and enrichment workflow.

The next phase focused on populating OpenCTI with additional external threat-intelligence data.

![OpenCTI Dashboard](screenshots/OpenCTI-Dashboard.png)
*Figure: OpenCTI  Dashboard with indicators populated.*


## Phase Two — Threat Intelligence Feed Integration

With OpenCTI deployed, the second phase focused on populating the platform with external threat intelligence that could later be used to enrich Wazuh security events.

Three intelligence sources were incorporated into the project:

- **URLhaus** — provided malicious URL and IP-based indicators.
- **AlienVault OTX** — provided threat intelligence through its collection of pulses and associated indicators.
- **MITRE ATT&CK** — provided structured adversary, malware, and attack-technique information.

![OpenCTI Threat Intelligence Sources](screenshots/ACTUAL-THREAT-INTELLIGENCE-FEEDS.png)

*Figure: OpenCTI threat-intelligence sources configured for the project.*

### URLhaus

URLhaus was used as a source of known malicious indicators. More than **900 indicators** were available from the feed and were later used to support indicator matching and validation.

### AlienVault OTX

AlienVault OTX was integrated to provide additional threat-intelligence context through its available pulses and indicators. The implementation retrieved **99 pulses**, providing a broader intelligence source for correlation within OpenCTI.

### MITRE ATT&CK

MITRE ATT&CK was used to provide structured relationships between adversaries, malware, and attack techniques. This allowed enrichment results to include ATT&CK context where applicable.

### ThreatFox

ThreatFox was considered as an additional intelligence source during the project but was **not included in the final implementation** because of the resource limitations of the laboratory environment.

### Phase Two Outcome

The completed feed configuration established OpenCTI as the central repository for the project's external threat intelligence.

The intelligence collected during this phase provided the data required for the next phase: building the custom **Wazuh-to-OpenCTI enrichment integration**.
