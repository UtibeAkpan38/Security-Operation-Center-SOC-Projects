# OBJECTIVE

The objective of this project is to design, implement, test, and validate a practical SOC detection and response workflow using Wazuh, Windows, Sysmon, and Atomic Red Team.

The project focuses on developing custom Wazuh detection rules for selected adversary behaviors mapped to the MITRE ATT&CK framework. Atomic Red Team is used to safely simulate these behaviors and generate security events on the monitored Windows endpoint.

In addition to detection engineering, a security incident response playbook was developed and used to provide a structured process for handling detected activities. The playbook guides the workflow from alert identification and validation through investigation, analysis, documentation, and recommended response actions.

The project therefore demonstrates an end-to-end SOC workflow:

Attack Simulation → Log Generation → SIEM Collection → Detection → Alert Analysis → Investigation → Playbook Execution → Documentation → Rule Tuning & Validation

The overall goal is to demonstrate how security monitoring, detection engineering, alert investigation, and incident response procedures can work together to identify and respond to simulated adversary activity within a controlled SOC environment.

# SCOPE

This project covers the development and validation of a controlled SOC detection and response environment focused on endpoint monitoring, security event detection, investigation, and incident response.

The scope of the project includes:

- Configuring and monitoring a Windows endpoint using Wazuh and Sysmon.
- Developing custom Wazuh detection rules for selected adversary behaviors.
- Mapping detected behaviors to relevant MITRE ATT&CK techniques.
- Using Atomic Red Team to safely simulate adversary techniques and generate security telemetry.
- Collecting and analyzing Windows security, Sysmon, and PowerShell event logs.
- Testing detection rules to determine whether simulated activities generate the expected alerts.
- Troubleshooting and tuning detection rules where expected alerts were not generated.
- Developing and applying an incident response playbook to provide a structured response process for detected activities.
- Documenting investigation findings, detection gaps, and improvements made during the testing process.
- Validating the final detection workflow through controlled testing.

The project is limited to a controlled laboratory environment. All attack simulations are performed against intentionally configured test systems for educational and detection-engineering purposes.

# LAB ENVIRONMENT AND ARCHITECHTURE

The project was conducted in a controlled virtualized SOC laboratory environment designed to simulate the monitoring and detection capabilities of a small Security Operations Center.

The environment consisted of a Windows endpoint monitored by Wazuh and Sysmon, with Atomic Red Team used to generate controlled adversary activity. The Wazuh infrastructure collected and analyzed security telemetry generated during the simulations, allowing custom detection rules to be tested and validated.

Environment Components

Wazuh Manager

The Wazuh Manager served as the central security monitoring and detection component of the lab. It received security events from the monitored Windows endpoint, processed the collected telemetry, and generated alerts based on configured detection rules.

Windows Endpoint

A Windows 11 virtual machine was used as the monitored endpoint. The system served as the target for controlled attack simulations and generated the Windows security and system telemetry required for detection and investigation.

Sysmon

Sysmon was deployed on the Windows endpoint to provide detailed telemetry about system activity, including process creation and other endpoint events. These logs provided additional visibility for developing and testing custom detection rules.

Atomic Red Team

Atomic Red Team was used to simulate selected MITRE ATT&CK techniques in a controlled manner. The simulations generated realistic endpoint activity that could be observed through Windows logs, Sysmon, and Wazuh.

Detection Rules

Custom Wazuh rules were developed to identify specific behaviors associated with the simulated techniques. The rules were tested against generated telemetry and tuned when the expected alerts were not produced.

Incident Response Playbook

An incident response playbook was created as part of the project to provide a structured procedure for responding to detected security events. The playbook was actively used during the investigation and response workflow rather than being created only as documentation.

Detection Workflow

The overall laboratory workflow was:

Atomic Red Team → Windows Endpoint → Sysmon / Windows Event Logs → Wazuh Agent → Wazuh Manager → Custom Detection Rules → Alert → Investigation → Incident Response Playbook → Documentation & Response

This architecture allowed the project to demonstrate the complete process of generating controlled adversary activity, collecting security telemetry, detecting suspicious behavior, investigating alerts, and following a structured response procedure.

# TOOLS AND TECHNOLOGIES 

The following tools and technologies were used throughout the project to build the detection, monitoring, simulation, investigation, and response workflow.

Tool / Technology| Purpose
Wazuh| SIEM and endpoint security monitoring platform used for log collection, alert generation, detection rules, and security event analysis.
Wazuh Agent| Installed on the Windows endpoint to collect and forward security telemetry to the Wazuh Manager.
Windows 11| Monitored endpoint used as the target system for controlled adversary simulations.
Sysmon| Provided detailed Windows endpoint telemetry, particularly process and system activity, for detection and investigation.
Atomic Red Team| Used to safely simulate selected MITRE ATT&CK techniques and generate test security events.
MITRE ATT&CK| Used as the framework for categorizing and mapping simulated adversary behaviors and detection rules.
PowerShell| Used during controlled attack simulations and analyzed as a source of endpoint telemetry.
Windows Event Logs| Provided security and system events used as detection and investigation data.
Incident Response Playbook| Provided a structured procedure for validating alerts, investigating activity, documenting findings, and determining response actions.
VirtualBox| Used to host and manage the virtual machines within the laboratory environment.

These technologies were combined to create an end-to-end detection and response workflow in which simulated adversary activity could be generated, observed, detected, investigated, and handled using a documented response procedure.
