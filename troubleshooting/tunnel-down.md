# Incident: SD-WAN Tunnel Down

**Date:** 5/12/2025  
**Affected Component:** FortiGate SD-WAN / IPsec Tunnels  
**Impact:** Branch offices lost connectivity to cloud resources.

---

## Incident Summary

The encrypted IPsec tunnel between branch FortiGate devices and the cloud hub went down, causing service disruption for multiple users.

---

## Root Cause Analysis

- Primary WAN link experienced intermittent failures.  
- IPsec tunnel configuration contained outdated parameters after a firmware update.  
- Firewall rules prevented failover traffic on secondary links.

---

## Resolution Steps

1. Verified physical connectivity and WAN link status.  
2. Updated IPsec tunnel configuration to match the current FortiGate firmware.  
3. Adjusted firewall rules to allow secondary link failover traffic.  
4. Monitored tunnel logs to ensure stable reconnection.  
5. Conducted failover testing to validate redundancy.

---

## Lessons Learned / Best Practices

- Maintain version-controlled configuration for SD-WAN tunnels.  
- Regularly test failover and redundancy paths.  
- Monitor tunnel health proactively to reduce downtime.
