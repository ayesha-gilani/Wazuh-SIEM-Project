# Wazuh-SIEM-Project

## 📝 1. Project Overview & Problem Statement
Modern IT systems face continuous security threats such as unauthorized access, brute-force attacks, malware execution, and file tampering. Traditional security solutions often fail to provide centralized monitoring and real-time alerting.

This project implements a Security Information and Event Management (SIEM) solution using **Wazuh** to monitor endpoints, detect suspicious activities, generate real-time alerts, and provide cross-platform visibility into system security events.

## 🎯 2. Objectives
* **Deploy** Wazuh SIEM on a Linux manager node.
* **Monitor** Windows and Linux endpoints concurrently.
* **Detect** authentication failures and simulated brute-force attacks.
* **Generate** real-time file tampering alerts using active agents.
* **Integrate** threat intelligence engines to catch potential malware indicators.
* **Audit** endpoint OS configurations against formal security baselines.

## 🛠️ 3. Tools & Technologies Used


| Category | Tools / Technologies |
| :--- | :--- |
| **SIEM Engine** | Wazuh Manager, Indexer, and Dashboard |
| **Monitored Nodes** | Ubuntu Server, Windows 10 Home/Pro |
| **Threat Intel** | VirusTotal API Integration |
| **Compliance Standards** | Security Configuration Assessment (SCA) - CIS Benchmarks |
| **Access Utilities** | SSH via MobaXterm |
| **Telemetry Formats** | Linux Syslog, Windows Security Event Logs |

---

## 🏗️ 4. System Architecture
The architecture consists of a central Wazuh Manager installed on an Ubuntu server that collects, parses, and analyzes security logs from distributed lightweight agents. Windows and Linux systems are configured as active endpoints forwarding system telemetry over secure channels to the Manager. Alerts are compiled and visualized using the web-based Wazuh Dashboard interface.

### Logical Data Flow
```text
[ Windows 10 Agent ] ───┐
                        ├───► [ Wazuh Manager ] ───► [ Dashboard Analytics ]
[ Ubuntu Endpoint  ] ───┘
```

---

## ⚙️ 5. Installation & Configuration Overview
1. **Wazuh Manager**: Set up and verified on an Ubuntu Server image.
2. **Endpoint Agents**: Installed and verified across target operating systems.
3. **FIM Modules**: Configured direct directory tracking hooks.
4. **Threat Intelligence**: Linked VirusTotal query blocks directly to the log parsing engine.

![Wazuh Server Status](screenshots/services_running.png)
*Figure: Verification of running operational services on the central Ubuntu manager node.*

---

## 🔍 6. Threat Monitoring & Event Generation (Use Cases Verified)

### 6.1 Authentication Failure & Brute Force Tracking
* **Methodology**: Executed consecutive unauthorized login attempts across Windows target nodes to generate security event generation sequences. Wazuh monitored the authentication event logs and flagged the malicious patterns.
* **Alert Proof**:
  ![Failed Login Event Log](screenshots/failed_login_alert.png)
  *Figure: Threat Hunting log stream capturing consecutive Windows Logon Failures (Rule ID 60122).*
### 6.2 Cross-Platform File Integrity Monitoring (FIM)
* **Methodology**: Modified configuration nodes on Linux targets and interacted with directories on Windows assets to verify real-time path monitoring behaviors.
* **Alert Proof**:
  ![Granular Event Timeline](screenshots/event_timeline.png)
  *Figure: Chronological event trace capturing active FIM metadata updates and file creation steps across endpoints.*

### 6.3 Threat Intelligence Enrichment (VirusTotal Integration)
* **Methodology**: Configured automatic hash evaluation pipelines. When files are modified inside monitored watchlists, file hashes are immediately transmitted to the VirusTotal engine to parse for malicious characteristics.
* **Alert Proof**:
  ![VirusTotal Detailed Alert Logs](screenshots/virustotal_alert_details.png)
  *Figure: Security log grid capturing VirusTotal API query actions (Rule IDs 87103, 87104) analyzing live file updates.*

### 6.4 Security Configuration Assessment (SCA) Compliance Audits
* **Methodology**: Enabled system baseline testing policies to score target node hardening states against verified regulatory industry definitions.
* **Alert Proof**:
  ![SCA Windows 10 CIS Benchmark Auditing](screenshots/sca_windows_compliance.png)
  *Figure: Windows 10 compliance engine metrics displaying hardening success rates against standard CIS Benchmarks.*

---

## 📊 7. Dashboard Analytics & Framework Mapping
### 7.1 Central Threat Hunting Control Plane
The main SIEM interface compiles incoming environment logs into high-level analytic boards mapping threat vectors directly to tactical frameworks.
![Wazuh Threat Hunting Dashboard Overview](screenshots/dashboard_overview.png)
*Figure: Threat hunting operational dashboard consolidating network security health metrics.*

### 7.2 MITRE ATT&CK Matrix Mapping
Incoming telemetry streams are automatically matched to structural threat categories within the open-source MITRE ATT&CK adversarial tracking framework.
![MITRE ATT&CK Framework Mapping Dashboard](screenshots/mitre_attack_dashboard.png)
*Figure: Graphic chart parsing active target endpoint behaviors into MITRE tactical designations.*

![MITRE ATT&CK Framework Matrix View](screenshots/mitre_attack_matrix.png)
*Figure: Structural matrix index detailing specific active adversarial techniques observed within the test environment.*

---

## 📈 8. Results & Outcomes
* **Unified Observability**: Established a functional centralized monitoring ecosystem ingestion matrix.
* **Proactive Defense Posture**: Automated malware identification routines via API scanning hooks.
* **Compliance Baselining**: Identified configuration weak points on assets using standardized CIS scoring.

## 🏁 9. Conclusion
This project demonstrates the deployment and maintenance parameters of an enterprise-grade SIEM engine across mixed operating system infrastructure environments. It successfully simulates core SOC security monitoring capabilities, tactical log ingestion workflows, and configuration auditing controls.
