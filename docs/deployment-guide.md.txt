# 🚀 SASE Deployment Guide  
**Prisma Access + Fortinet SD-WAN**

---

## 📌 Objective
Deploy a production-grade SASE architecture enabling:
- Secure remote user access (ZTNA)
- Branch connectivity via SD-WAN
- Centralized security enforcement using Prisma Access

---

## 🧱 Architecture Components

| Component | Role |
|----------|------|
| Prisma Access | Cloud security (ZTNA, SWG, CASB, DLP) |
| FortiGate SD-WAN | Branch routing and traffic steering |
| Identity Provider (IdP) | User authentication |
| SaaS Applications | End applications (e.g., Salesforce, O365) |

---

## 🛠️ Prerequisites

### Network Requirements
- Public IP for FortiGate WAN  
- Internet connectivity  
- DNS configured  

### Prisma Access
- Tenant activated  
- Admin access available  

### FortiGate
- Firmware updated  
- SD-WAN enabled  

---

## ⚙️ Step 1: Prisma Access Setup

### 1. Login
Access Prisma Cloud portal

### 2. Configure Remote Networks
- Navigate: Prisma Access → Remote Networks  
- Add new site:
  - Name: Branch-1  
  - Region: Closest location  
  - Bandwidth: As per requirement  

### 3. Configure Security Policies
- Navigate: Policies → Security  
- Create rules:
  - Allow SaaS traffic  
  - Block malicious traffic  

### 4. Enable ZTNA
- Navigate: Access → ZTNA  
- Configure:
  - User group  
  - Applications  
  - Access policies  

---

## ⚙️ Step 2: FortiGate SD-WAN Configuration

### Enable SD-WAN
```bash
config system sdwan
    set status enable
end

Configure WAN Interfaces

WAN1 → ISP1
WAN2 → ISP2

Create SD-WAN Rule

config system sdwan service
    edit 1
        set name "SaaS-Traffic"
        set dst "all"
        set priority-members 1 2
    next
end

Step 3: IPSec Tunnel (FortiGate → Prisma)

Phase 1

config vpn ipsec phase1-interface
    edit "Prisma-Tunnel"
        set interface "wan1"
        set remote-gw <PRISMA-IP>
        set psksecret <your-psk>
    next
end

Phase 2

config vpn ipsec phase2-interface
    edit "Prisma-P2"
        set phase1name "Prisma-Tunnel"
        set proposal aes256-sha256
    next
end

Step 4: Routing Configuration

Static Route

config router static
    edit 1
        set dst 0.0.0.0/0
        set device "Prisma-Tunnel"
    next
end

Step 5: Traffic Steering

Route SaaS traffic via Prisma Access
Route internal traffic to Data Center

Step 6: Validation

Check Tunnel Status

get vpn ipsec tunnel summary

Test Connectivity

Ping Prisma gateway
Access SaaS applications

Verify Logs

FortiGate logs
Prisma Access logs