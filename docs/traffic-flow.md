# 🔄 Traffic Flow Explanation

## 👤 Remote User Flow
User → Prisma Access → Policy Check → SaaS

Step-by-step:
1. User initiates connection
2. Authenticated via IdP
3. ZTNA policies applied
4. Traffic forwarded securely

---

## 🏢 Branch Flow
Branch → FortiGate → SD-WAN → IPSec → Prisma

Step-by-step:
1. Traffic enters FortiGate
2. SD-WAN evaluates best path
3. Tunnel established to Prisma
4. Security inspection enforced