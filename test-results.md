# Connectivity Test Results

Based on the screenshots currently included in this repository. A failed ping is recorded as failed; no assumption is made about the intended ACL policy.

| Source | Destination | Observed result |
|---|---|---|
| PC-IT | `192.168.30.1` (IT gateway) | Pass — 4/4 replies |
| PC-IT | `192.168.20.10` (Finance PC) | Pass — 4/4 replies |
| PC-HR | `192.168.30.10` (IT PC) | Pass — 4/4 replies |
| PC-HR | `192.168.20.10` (Finance PC) | Fail — 4/4 lost; destination host unreachable from `192.168.10.1` |
| PC-Finance | `192.168.10.10` (HR PC) | Fail — 4/4 lost; destination host unreachable from `192.168.20.1` |

## Interpretation

The evidence confirms that some cross-VLAN communication works, while HR–Finance traffic does not. The router screenshots show ACLs applied inbound on the HR and Finance subinterfaces. Inspect the ACL entries and confirm the intended policy before concluding whether the failures are expected security behavior or a configuration problem.
