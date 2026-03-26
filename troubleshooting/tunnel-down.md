# 🚨 IPSec Tunnel Down

## Symptoms
- Tunnel not established
- No traffic flow

## Checks
- Verify Phase1 configuration
- Check PSK
- Validate ISP connectivity

## Debug Commands
diag debug application ike -1
diag debug enable

## Fix
- Correct PSK
- Restart tunnel
- Validate peer IP