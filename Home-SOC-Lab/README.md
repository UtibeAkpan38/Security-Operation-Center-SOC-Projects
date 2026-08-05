# Home SOC Lab

## Overview

This project documents the design, deployment, and expansion of a Security Operations Center (SOC) home lab built for hands-on blue team training, threat detection, log analysis, and incident investigation.

The lab simulates a small enterprise environment using Wazuh as the central SIEM platform, integrated with multiple security tools to provide endpoint monitoring, network visibility, threat intelligence enrichment, and custom detection capabilities.

## Project Objectives

- Build a functional SOC home lab using virtual machines.
- Collect and centralize logs from multiple endpoints.
- Develop and test custom Wazuh correlation rules.
- Simulate attacks and validate detection capabilities.
- Create dashboards for monitoring security events.

## Lab Architecture

The lab consists of the following components:

- *Hypervisor:* Oracle VirtualBox
- *Host Operating System:* Windows 11
- *Wazuh Manager:* Kali Linux
- *Endpoint 1:* Ubuntu Server with Wazuh Agent and Suricata
- *Endpoint 2:* Windows 11 with Wazuh Agent and Sysmon
- *Firewall:* pfSense
- *Threat Intelligence:* VirusTotal Integration

### Architecture Diagram
! [SOC Home Lab Architecture](images/architecture.jpeg
