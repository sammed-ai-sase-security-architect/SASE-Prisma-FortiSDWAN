# Incident: Application Access Failure

**Date:** 25/11/2025  
**Affected Component:** Prisma SASE / Branch SD-WAN  
**Impact:** Users unable to access a critical application from branch office.

---

## Incident Summary

Branch users reported that they could not access the enterprise application hosted in the cloud. Attempts from multiple devices failed, indicating a policy or routing issue.

---

## Root Cause Analysis

- Zero Trust Network Access (ZTNA) policies in Prisma SASE were misconfigured.  
- Application traffic was incorrectly blocked due to a policy mismatch.  
- Routing rules in FortiSDWAN did not direct traffic through the secure tunnel.

---

## Resolution Steps

1. Reviewed Prisma SASE access policies for the affected application.  
2. Updated ZTNA policy to allow authenticated users access to the application.  
3. Verified SD-WAN routing configuration on FortiGate for proper tunnel selection.  
4. Tested application access from multiple branch endpoints.  
5. Confirmed logs showed successful traffic flow to the cloud application.

---

## Lessons Learned / Best Practices

- Always validate ZTNA policies after deployment or policy updates.  
- Monitor access logs proactively to detect misconfigurations early.  
- Document traffic flows per application to simplify troubleshooting.
