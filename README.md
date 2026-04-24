### Detection-ELK

### Objectives

This project addresses the challenge of detecting SSH brute-force attacks and abnormal system activity across Linux and Windows systems by centralizing and analysing security logs with an ELK-based SIEM to enable real-time threat detection.

Tools used
- AWS EC2
  - Elasticsearch, Log Stach, Kibana - ELK on Ubuntu 24.04 
  - Ubuntu 24.04 Client
  - Window 2022
  - Ubuntu 24.04 attacker
    
### Architecture

```mermaid
flowchart TB
    subgraph AWS["AWS EC2 Environment"]

        subgraph A["Attacker (Ubuntu 24.04)"]
            A1[SSH/RDP Attack Script]
        end

        subgraph T["Targets"]
            T1[Ubuntu Client]
            T2[Windows Server 2022]
        end

        subgraph E["ELK Stack (Ubuntu 24.04)"]
            L[Logstash]
            ES[Elasticsearch]
            K[Kibana]
        end

    end

    A1 -->|Brute Force SSH| T1
    A1 -->|Login Attempts| T2

    T1 -->|/var/log/auth.log| L
    T2 -->|Windows Event Logs| L

    L --> ES
    ES --> K


```
ELK Installation
