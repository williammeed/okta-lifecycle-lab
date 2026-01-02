# Okta Life-Cycle Lab  
*Identity-first onboarding & off-boarding for SaaS teams*

---

## 1. Objective
Automate the full user life-cycle in a modern, SaaS-only stack:
- Provision → Google Workspace + Slack + MFA in one Okta action.
- De-provision → instant suspension, license reclaim, audit trail.
- Document Tier-1 ready runbooks and real ticket metrics.

---

## 2. Lab Inventory
| Component | Tier / Limit | Link / Note |
|-----------|--------------|-------------|
| Okta | Integrator Free – 10 users | `https://okta-lab-williammeed.okta.com` |
| Google Workspace | Business Starter trial | Domain: `lab-williammeed.com` |
| Slack | Free workspace | `okta-lab-williammeed.slack.com` |
| Jira Service Mgmt | Free | Project key `OKTA-LAB` |
| Test fleet | 1 macOS VM, 1 Win-11 VM | Used for MFA & device trust smoke-tests |

---

## 3. Runbooks
### 3.1 New-Hire Onboarding *(≤ 15 min hands-on)*
1. **Jira** – create `onboarding/&lt;first.last&gt;` ticket.
2. **Okta** – Directory → People → Add Person  
   - Email: `first.last@lab-williammeed.com`  
   - Groups: `employee` + `engineering` *(auto-assigns apps)*
3. **Automation** *(SCIM)*  
   - Google Workspace – account + license created.  
   - Slack – user invited to `#general`.
4. **Okta** – Reset password → activation email *(forces MFA enroll)*.
5. **Verify**  
   - ✓ Gmail inbox loads.  
   - ✓ Slack shows “Active” in admin panel.
6. **Jira** – close ticket with timestamp & screenshot.

### 3.2 Same-Day Off-boarding *(≤ 10 min)*
1. **Jira** – `offboarding/&lt;first.last&gt;` ticket.
2. **Okta** – suspend user → Google & Slack auto-revoked.
3. *(Optional)* – transfer Google Drive files to manager.
4. **Security** – wipe MFA factors.
5. **Evidence** – export Google & Slack audit logs → attach to ticket → close.

---

## 4. Ticket Simulation
| Ticket ID | Summary | Work Log | Evidence |
|-----------|---------|----------|----------|
| **ONBOARD-1** | New sales rep (Ada Lovelace) | 8 min 04 sec | [onboard-demo.mp4](evidence/onboard-demo.mp4) |
| **OFFBOARD-1** | Same-day termination | 5 min 11 sec | [google_audit.csv](evidence/google_offboard_audit.csv) [slack_audit.csv](evidence/slack_offboard_audit.csv) |

---

## 5. Metrics & Evidence
- **Onboarding** – 8 min 04 sec *(video)*  
- **Off-boarding** – 5 min 11 sec  
- **Manual steps in Google/Slack** – 0  
- **MFA enrollment** – 100 % *(10/10 users)*  
- **Audit exports** – SOC-2 style paper trail attached for every off-board.
