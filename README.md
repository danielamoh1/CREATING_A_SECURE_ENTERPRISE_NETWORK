# CREATING_A_SECURE_ENTERPRISE_NETWORK

```mermaid
flowchart TD;

    %% Grouping the firewall functionalities under one subgraph
    subgraph Perimeter Firewall Setup
        A1[pfsense/OPNsense] --> B1[Firewall Zones and Policies]
        A1 --> C1[NAT Configuration]
        B1 --> D1[Traffic Shaping and QoS]
    end

    %% IDS/IPS section using Suricata
    subgraph Intrusion Detection/Prevention
        A2[Suricata] --> B2[Intrusion Detection]
        A2 --> C2[Intrusion Prevention]
    end
    
    %% VPN and Remote Access section using OpenVPN
    subgraph VPN Setup
        A3[OpenVPN] --> B3[Remote Access VPN for Employees]
        A3 --> C3[Site-to-Site VPN]
    end

    %% High Availability setup using CARP
    subgraph High Availability and Failover
        A4[CARP for HA] --> B4[Active/Passive Failover]
    end
    
    %% Centralized logging and monitoring using ELK stack or Graylog
    subgraph Centralized Logging & Monitoring
        A5[ELK Stack/Graylog] --> B5[Firewall Logs]
        A5 --> C5[Suricata Logs]
    end

    %% Connecting Components together
    Perimeter Firewall Setup --> Intrusion Detection/Prevention
    Perimeter Firewall Setup --> VPN Setup
    Intrusion Detection/Prevention --> High Availability and Failover
    VPN Setup --> Centralized Logging & Monitoring
    High Availability and Failover --> Centralized Logging & Monitoring

    %% Labeling references for proprietary solutions
    subgraph PaloAlto Fortinet JuniperSRX References
        X1[Palo Alto: Zones & Policies, App-ID, GlobalProtect] --> A1
        X2[Fortinet: Zones, IPS, FortiGuard] --> A2
        X3[Juniper: AppSecure, SRX QoS] --> A4
    end
```
