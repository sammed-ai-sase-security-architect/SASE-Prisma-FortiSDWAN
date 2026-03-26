# Incident: Zero Trust Access (ZTNA) Issues

**Date:** 2/3/2026  
**Affected Component:** Prisma SASE / ZTNA  
**Impact:** Users unable to reach protected applications despite valid credentials.

---

## Incident Summary

Authenticated users were denied access to critical enterprise applications, indicating a misalignment in Zero Trust policies or user/device profiles.

---

## Root Cause Analysis

- ZTNA micro-segmentation policy did not include the affected user group.  
- Device compliance checks failed due to outdated endpoint security software.  
- Policy propagation delays caused temporary denial across branches.

---

## Resolution Steps

1. Reviewed ZTNA micro-segmentation policies in Prisma Access.  
2. Added the affected user group to the appropriate application policy.  
3. Ensured all endpoints met compliance requirements (antivirus, patch levels).  
4. Validated policy propagation across all branch gateways.  
5. Tested access for multiple users and devices.

---

## Lessons Learned / Best Practices

- Maintain up-to-date device compliance policies for Zero Trust access.  
- Include all user groups in ZTNA policy templates.  
- Regularly audit policy propagation and logs to catch inconsistencies early.
