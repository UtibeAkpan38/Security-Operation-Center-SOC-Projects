# OBJECTIVE

The objective of this project was to investigate a suspicious network indicator associated with unusual outbound activity from a monitored workstation.

The investigation focused on the IP address 185.220.101.47, which was observed making repeated outbound connections to workstation WS-FINANCE-04 on port 443 at 02:14 AM, outside normal business hours. The session lasted approximately 18 minutes and transferred 4.2 MB of data outbound, while no user was logged into the workstation.

The investigation involved using threat intelligence platforms to classify and assess the indicator, mapping the observed behavior to relevant MITRE ATT&CK techniques, analyzing the indicator using the Pyramid of Pain, and determining appropriate containment and long-term security recommendations.

The overall objective was to demonstrate a practical SOC Tier-1 threat intelligence investigation workflow, from initial IOC analysis through threat classification, ATT&CK mapping, risk assessment, and recommended response actions.


# SCOPE

This investigation focused on analyzing a suspicious external IP address identified through network activity from a monitored workstation.

The investigation covered:

- Identification and analysis of the suspicious IP address 185.220.101.47.
- Investigation of the indicator using VirusTotal and AbuseIPDB.
- Examination of the IP's reputation, threat classification, and associated infrastructure.
- Analysis of the observed outbound connection from workstation WS-FINANCE-04.
- Review of the connection timing, duration, destination port, and outbound data volume.
- Assessment of the indicator using the Pyramid of Pain framework.
- Mapping of observed attacker behavior to relevant MITRE ATT&CK techniques.
- Determination of the potential security impact of the activity.
- Development of recommended containment, eradication, and long-term security measures.

The investigation was performed from a SOC Tier-1 analyst perspective, with emphasis on threat intelligence analysis, IOC validation, behavioral assessment, and providing actionable recommendations for further investigation and response.

# TOOLS AND TECHNOLOGIES

The following tools and frameworks were used during the threat intelligence investigation:

- VirusTotal — Used to investigate the suspicious IP address, review threat intelligence detections, and identify associated malicious activity and infrastructure.
- AbuseIPDB — Used to assess the reputation of the suspicious IP address and review abuse reports associated with the indicator.
- MITRE ATT&CK — Used to map observed adversary behavior to relevant tactics and techniques.
- Pyramid of Pain — Used as a framework for evaluating the value and difficulty of different types of indicators from an adversary's perspective.
- Network Traffic Analysis — Used to examine the suspicious outbound connection, including the destination, connection duration, port, and amount of outbound data transferred.

These tools and frameworks were combined to support an end-to-end threat intelligence workflow, from initial IOC investigation and reputation analysis through behavioral assessment, MITRE ATT&CK mapping, risk evaluation, and recommended response actions.

# INVESTIGATION METHODOLOGY

The investigation followed a structured threat intelligence workflow designed to validate the suspicious indicator, determine its risk level, understand the associated activity, and identify appropriate response actions.

1. Initial IOC Identification

The investigation began after a suspicious external IP address, 185.220.101.47, was identified in network activity involving the monitored workstation WS-FINANCE-04.

The activity was considered suspicious because the workstation established repeated outbound connections to the external IP address on TCP port 443 at approximately 02:14 AM, outside normal business hours.

The observed session lasted approximately 18 minutes and involved approximately 4.2 MB of outbound data, despite there being no active user session on the workstation.

2. Threat Intelligence Enrichment

The suspicious IP address was investigated using external threat intelligence sources.

VirusTotal was used to determine whether the indicator had been identified or associated with malicious activity by security vendors and threat intelligence sources.

AbuseIPDB was used to examine the reputation of the IP address and review reports associated with potentially abusive or malicious activity.

The intelligence gathered from these sources was used to determine whether the indicator represented a known threat and to provide additional context around the observed network activity.

3. Indicator Classification

The investigation assessed the IP address based on the available intelligence and observed network behavior.

The indicator was identified as being associated with Tor infrastructure, specifically a Tor exit node. The IP address also had a high abuse reputation, with an AbuseIPDB confidence score of 99%.

This increased the risk associated with the repeated outbound communication and warranted further investigation.

4. Behavioral Analysis

The observed network activity was analyzed to determine whether the connection pattern was consistent with potentially malicious behavior.

Key observations included:

- Repeated outbound communication to the suspicious IP address.
- Communication over TCP port 443.
- Activity occurring at approximately 02:14 AM.
- A session duration of approximately 18 minutes.
- Approximately 4.2 MB of outbound data transferred.
- No user logged into the workstation during the observed activity.

These observations were considered collectively rather than treating the IP reputation alone as evidence of compromise.

5. MITRE ATT&CK Mapping

The observed behavior was mapped to the MITRE ATT&CK framework to provide a standardized description of the potential adversary activity.

The investigation considered the observed outbound communication and potential data transfer behavior when determining the most appropriate ATT&CK techniques.

The mapping provided additional context for understanding the potential objective of the activity and supported the development of appropriate detection and response measures.

6. Pyramid of Pain Assessment

The Pyramid of Pain framework was used to evaluate the intelligence value of the identified indicator.

The analysis considered the difference between easily changed indicators, such as IP addresses and hashes, and higher-level indicators such as tools, tactics, techniques, and procedures.

This helped establish how useful the identified IOC could be for defensive detection and how easily an adversary could change or replace it.

7. Risk Assessment and Response Recommendations

The final stage of the investigation involved assessing the potential security impact of the activity and developing recommended response actions.

The recommendations focused on:

- Investigating the affected workstation for signs of compromise.
- Blocking or restricting communication with the suspicious indicator where appropriate.
- Reviewing additional network and endpoint telemetry.
- Searching for related indicators across the environment.
- Determining whether data exfiltration or unauthorized access occurred.
- Strengthening monitoring and detection for similar activity.
- Maintaining relevant indicators for future threat hunting.

The investigation therefore progressed from IOC identification → threat intelligence enrichment → indicator classification → behavioral analysis → ATT&CK mapping → Pyramid of Pain assessment → risk assessment and response recommendations.

# INVESTIGATION FINDINGS

The investigation produced several findings that increased the confidence that the observed network activity required security investigation and response.

1. Suspicious IP Address

The primary indicator investigated was:

- IP Address: "185.220.101.47"
- Associated Infrastructure: Tor Exit Node
- Observed Destination Port: TCP/443
- Affected Workstation: WS-FINANCE-04
- Observed Time: Approximately 02:14 AM
- Session Duration: Approximately 18 minutes
- Outbound Data: Approximately 4.2 MB

The combination of the indicator's reputation and the unusual communication pattern made the connection worthy of further investigation.

2. VirusTotal Intelligence

The suspicious IP address was investigated using VirusTotal to identify existing security intelligence associated with the indicator.

The investigation showed that the IP address had associations with suspicious or malicious activity and provided additional context that supported the decision to treat the indicator as potentially malicious.

VirusTotal was therefore used as an initial enrichment source rather than relying solely on the presence of an IP address in a threat intelligence database.

3. AbuseIPDB Reputation

The IP address was also investigated using AbuseIPDB.

The indicator received an AbuseIPDB confidence score of 99%, indicating a very high level of reported abuse associated with the address.

This reputation score provided additional evidence that the external IP address should be treated as a high-risk indicator during the investigation.

4. Tor Exit Node Identification

The investigation identified 185.220.101.47 as a Tor exit node.

Tor exit nodes can be used for legitimate privacy purposes, so the presence of a Tor exit node alone does not prove malicious activity.

However, in this investigation, the Tor association was considered alongside the other observations, including repeated outbound communication, the unusual time of activity, the absence of an active user session, and the volume of outbound data.

5. Unusual Outbound Communication

The workstation WS-FINANCE-04 established repeated outbound communication with the suspicious IP address over TCP port 443.

Although HTTPS traffic over port 443 is common and normally expected, the timing and context of this particular communication made it anomalous.

The activity occurred at approximately 02:14 AM, outside normal business hours, and the workstation had no active user logged in at the time.

6. Potential Data Transfer

The observed session lasted approximately 18 minutes and transferred approximately 4.2 MB of data outbound.

The outbound direction of the traffic was particularly relevant because it raised the possibility that information could have been transmitted from the workstation to the external destination.

The available evidence was not sufficient by itself to confirm successful data exfiltration. Therefore, the finding was treated as a potential data-transfer concern requiring additional investigation.

7. Overall Assessment

The individual indicators were evaluated collectively rather than in isolation.

The combination of:

- A high-reputation-risk external IP address.
- Identification as a Tor exit node.
- Repeated outbound connections.
- Communication over TCP/443.
- Activity occurring outside normal business hours.
- No active user session.
- Approximately 18 minutes of communication.
- Approximately 4.2 MB of outbound data.

resulted in the activity being assessed as suspicious and requiring further investigation and appropriate containment measures.

The investigation did not rely solely on IP reputation to determine maliciousness. Instead, threat intelligence, network context, timing, and observed behavior were correlated to produce a more reliable assessment.

# MITRE ATT&CK MAPPING

The observed activity was mapped to the MITRE ATT&CK framework to provide a standardized representation of the potential adversary behavior identified during the investigation.

Exfiltration Over C2 Channel — T1041

The observed outbound communication and transfer of approximately 4.2 MB of data to an external destination were assessed against the ATT&CK technique T1041 — Exfiltration Over C2 Channel.

This technique describes the transfer of collected information from a compromised system to an external destination through an existing command-and-control communication channel.

The available evidence did not independently confirm the exact contents of the transferred data or conclusively establish successful data exfiltration. However, the outbound communication pattern and data transfer were sufficient to warrant investigation for potential exfiltration activity.

Scheduled Transfer — T1029

The observed communication pattern was also considered in relation to T1029 — Scheduled Transfer.

This technique involves an adversary transferring data according to a predefined schedule or timing mechanism to reduce the likelihood of detection.

The observed activity occurring at approximately 02:14 AM, outside normal business hours, was considered relevant to this technique. However, additional endpoint evidence would be required to establish whether an actual scheduled mechanism was responsible for the transfer.

MITRE ATT&CK mapping was therefore used as a behavioral classification and investigative aid rather than as definitive proof that a specific technique was successfully executed.

---

# PYRAMID OF PAIN ANALYSIS

The Pyramid of Pain framework was used to evaluate the defensive value of the intelligence collected during the investigation.

The primary indicator identified was the suspicious IP address 185.220.101.47.

Hashes

No specific file hash was established as the primary indicator during this investigation.

IP Address

The suspicious IP address represented a low-level IOC that can be blocked relatively easily but can also be changed by an adversary.

Blocking the identified IP could help prevent communication with the known destination, but it would not necessarily prevent an adversary from using another infrastructure address.

Domain Names

No specific malicious domain was established as the primary indicator during the investigation.

Network/Host Artifacts

The investigation included behavioral observations such as repeated outbound connections, communication over TCP/443, unusual connection timing, and outbound data transfer.

These observations can provide additional detection opportunities beyond simply blocking the IP address.

Tools

The investigation identified the use of Tor infrastructure, specifically a Tor exit node.

While Tor itself is not inherently malicious, identifying infrastructure and tools associated with suspicious activity can provide additional context for threat hunting and detection.

Tactics, Techniques, and Procedures

The highest-value intelligence came from understanding the behavior rather than relying exclusively on the IP address.

The investigation considered potential data transfer and exfiltration behavior and mapped the activity to relevant MITRE ATT&CK techniques.

This behavioral intelligence is more difficult for an adversary to change than a single IP address and can therefore provide stronger long-term defensive value.

---

# RISK ASSESSMENT

Based on the available intelligence and observed network behavior, the activity was assessed as highly suspicious and requiring further investigation.

The risk assessment was based on the combination of:

- High abuse reputation associated with the IP address.
- Identification of the IP as a Tor exit node.
- Repeated outbound communication.
- Unusual activity occurring at approximately 02:14 AM.
- No active user session on the affected workstation.
- Approximately 18 minutes of communication.
- Approximately 4.2 MB of outbound data transfer.

The evidence did not independently prove that the workstation was compromised or that sensitive information was successfully exfiltrated. However, the combination of indicators justified treating the activity as a potential security incident until additional evidence could confirm or eliminate that possibility.

---

# RECOMMENDATIONS

Based on the findings, the following actions were recommended:

Immediate Actions

1. Investigate WS-FINANCE-04 for signs of compromise, including suspicious processes, persistence mechanisms, unusual files, and unauthorized configuration changes.

2. Review endpoint telemetry around the time of the suspicious connection to identify the process responsible for communicating with the external IP address.

3. Block or restrict communication with "185.220.101.47" where appropriate.

4. Search the environment for additional systems communicating with the same IP address.

5. Review network logs and proxy/firewall telemetry for related connections and indicators.

Further Investigation

6. Determine whether the approximately 4.2 MB outbound transfer contained sensitive or unauthorized data.

7. Investigate whether the communication was generated by legitimate software or an unauthorized process.

8. Search for additional Tor-related activity across the environment.

9. Review authentication and endpoint activity around the time of the connection.

10. Preserve relevant logs and evidence for further investigation if compromise is suspected.

Long-Term Improvements

11. Develop detections for unusual outbound connections occurring outside normal business hours.

12. Monitor for repeated communication with known malicious or high-risk infrastructure.

13. Establish threat intelligence enrichment within the SOC workflow to improve IOC investigation.

14. Use behavioral detections in addition to simple IOC blocking to reduce dependence on easily changed indicators.

15. Continue mapping suspicious activity to MITRE ATT&CK to improve detection coverage and threat hunting.

---

# INVESTIGATION LIMITATIONS

Several limitations were identified during the investigation.

- The available evidence did not confirm the exact contents of the outbound data.
- The investigation could not independently establish whether the workstation was compromised.
- Identification of a Tor exit node does not, by itself, establish malicious activity.
- The available network evidence did not conclusively identify the process responsible for the connection.
- Additional endpoint, firewall, proxy, and authentication logs would be required for deeper correlation.
- MITRE ATT&CK mappings represent behavioral assessments and should be validated with additional evidence before being treated as confirmed techniques.

These limitations highlight the importance of correlating threat intelligence with endpoint and network telemetry during SOC investigations.

---

# CONCLUSION

This investigation demonstrated a practical threat intelligence workflow for analyzing a suspicious external indicator and determining its potential security impact.

The investigation began with the identification of 185.220.101.47 communicating with WS-FINANCE-04 over TCP/443 at approximately 02:14 AM. Threat intelligence enrichment identified the address as a Tor exit node and revealed a 99% AbuseIPDB confidence score, increasing the concern surrounding the activity.

Additional analysis showed repeated outbound communication lasting approximately 18 minutes with approximately 4.2 MB of outbound data transferred while no user was logged into the workstation.

The activity was evaluated using threat intelligence sources, behavioral analysis, the Pyramid of Pain, and MITRE ATT&CK mapping. The evidence did not conclusively prove compromise or successful data exfiltration, but the combination of indicators was sufficiently suspicious to justify further investigation and containment.

The investigation demonstrates that effective SOC analysis should not rely on a single IOC or reputation score. Instead, analysts should correlate threat intelligence, network behavior, timing, endpoint context, and adversary techniques to produce a more accurate assessment and actionable response.

Overall, the project provided practical experience in IOC investigation, threat intelligence enrichment, behavioral analysis, ATT&CK mapping, risk assessment, and SOC response recommendations.
