# 📋 ENTERPRISE NETWORK CHANGE REQUEST (CR) / ÄNDERUNGSANTRAG
**Standard:** ITIL 4 Change Enablement & NIST SP 800-128 Compliant
**Reference ID:** CR-${YEAR}-${UUID}
**Classification:** Internal / Confidential

---

## I. CHANGE OVERVIEW (ÜBERSICHT)
*   **Requestor / Owner:** Abbas Sadeghifard (Network Engineer)
*   **Impact Level / Criticality:** [ ] Low (Standard)  |  [ ] Medium  |  [ ] High (Major Change)
*   **Target Devices / Hostnames:**
    *   *Core Switch:* `DE-MUC-SW01` (Cisco Catalyst 9300)
    *   *Firewall:* `DE-MUC-FW01` (FortiGate 100F)
*   **Change Window (Zeitfenster):**
    *   *Start:* YYYY-MM-DD HH:MM (UTC/CET)
    *   *End:* YYYY-MM-DD HH:MM (UTC/CET)
*   **Summary of Change:**
    > _Describe the business and technical goals (e.g., Implementing VLAN 50 for local lab isolation and applying security policies on FortiGate)._

---

## II. RISK ASSESSMENT & DEPENDENCIES (RISIKOANALYSE)
*   **Impact Score (1-5):** [ ]
*   **Probability of Failure (1-5):** [ ]
*   **Downstream Dependencies:**
    *   Does this change affect Active Directory (AD) replication? [Yes/No]
    *   Is there an active backup job running during the service window? [Yes/No]
*   **Service Interruption (Downtime required?):** [ ] No Downtime (Hitless)  |  [ ] Temporary (Under 5 mins)  |  [ ] Full Outage

---

## III. PRE-IMPLEMENTATION / THE SNAPSHOT (VORBEREITUNG)
*Before typing a single configuration command, you MUST take state snapshots and backups.*

### 1. Configuration Backup (Datensicherung)
*   **Cisco IOS-XE:**
```ios
copy running-config flash:CR-${YEAR}-${UUID}-pre-backup.cfg
! Or TFTP backup:
copy running-config tftp://10.10.10.250/DE-MUC-SW01-pre.cfg
```

*   **FortiGate (FortiOS):**
```bash
# Via CLI:
execute backup config tftp DE-MUC-FW01-pre.conf 10.10.10.250
# Or via GUI: System > Firmware/Config > Backup Configuration
```

### 2. State Verification Snapshot
Capture baseline outputs to compare against post-change state:
```ios
show vlan brief
show interface status
show spanning-tree summary
show ip route summary
show cdp neighbors
```
```bash
get system status
get router info routing-table all
diagnose sys session list
```

### 3. Pre-Checks Checklist
*   [ ] Backups stored in two locations (local flash + TFTP/SFTP server)
*   [ ] Maintenance window communicated to stakeholders
*   [ ] On-call / second engineer notified and available
*   [ ] Rollback plan reviewed and understood by all parties
*   [ ] Console / out-of-band access confirmed (in case of network loss)

---

## IV. IMPLEMENTATION PLAN (UMSETZUNG)
*List exact, sequential commands. No ambiguity — each step should be copy-paste ready.*

| Step | Device | Action | Command / Reference |
|------|--------|--------|----------------------|
| 1 | DE-MUC-SW01 | Create VLAN 50 | `vlan 50` `name LAB-ISOLATION` |
| 2 | DE-MUC-SW01 | Assign port to VLAN | `interface GigX/X` `switchport access vlan 50` |
| 3 | DE-MUC-FW01 | Create interface/VLAN | *(per FortiOS GUI/CLI syntax)* |
| 4 | DE-MUC-FW01 | Apply security policy | *(per FortiOS GUI/CLI syntax)* |
| 5 | — | Save configuration | `write memory` / `execute config save` |

---

## V. VALIDATION / POST-IMPLEMENTATION (ÜBERPRÜFUNG)
*   **Functional Tests:**
    *   [ ] Ping connectivity test between affected segments
    *   [ ] Verify VLAN appears in `show vlan brief`
    *   [ ] Confirm firewall policy hit counts increment as expected
    *   [ ] Re-run baseline commands from Section III.2 and diff against pre-change state
*   **Stakeholder Sign-off:**
    *   [ ] Requestor confirms change meets business requirement
    *   [ ] Network Lead / Change Approver confirms no anomalies

---

## VI. ROLLBACK PLAN (RÜCKFALLPLAN)
*Define BEFORE implementation. Trigger criteria + exact restore steps.*

*   **Rollback Trigger Criteria:** _(e.g., loss of connectivity >5 min, routing instability, failed validation tests)_
*   **Rollback Steps:**
```ios
configure replace flash:CR-${YEAR}-${UUID}-pre-backup.cfg force
```
```bash
execute restore config tftp DE-MUC-FW01-pre.conf 10.10.10.250
```
*   **Rollback Validation:** Repeat Section V tests post-rollback to confirm restoration of original state.
*   **Maximum Time to Decide on Rollback:** _____ minutes after window start

---

## VII. APPROVALS (GENEHMIGUNGEN)

| Role | Name | Signature / Approval | Date |
|------|------|----------------------|------|
| Requestor | Abbas Sadeghifard | | |
| Change Approver / CAB | | | |
| Technical Reviewer | | | |

---

## VIII. POST-CHANGE REVIEW (NACHBEREITUNG)
*   **Outcome:** [ ] Successful  |  [ ] Successful with Issues  |  [ ] Rolled Back  |  [ ] Failed
*   **Actual Start/End Time:**
*   **Lessons Learned / Notes:**
    > _Document any deviations from plan, unexpected behavior, or follow-up actions required._
*   **CR Closed By:** _____________  **Date:** _____________
