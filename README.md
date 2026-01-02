# okta-lifecycle-lab
okta user lifecycle lab

**1. Objectives:**

Demonstrate end-to-end user life-cycle in a SaaS-first stack:
- Provision a new hire in Okta → auto-create Google Workspace account → auto-license Slack → enforce MFA.
- Reverse the flow for termination (suspend Okta → disable Google → revoke Slack).
- Track time-on-task and document runbook for Tier-1 hand-off.

**2. Inventory:**
- Okta Integrator Free Org (10-user limit) – `okta-lab-&lt;your-handle&gt;.okta.com`
- Google Workspace Business Starter (14-day trial) – primary domain `lab-&lt;your-handle&gt;.com` (Google Domains $12/yr)
- Slack free workspace – `okta-lab-&lt;your-handle&gt;.slack.com`
- Test macOS VM (Monterey or later) for MFA enroll smoke-test
- Jira Service Management free tier – project key `OKTA-LAB`
  
**3. Runbooks:**

## New-Hire Onboarding (Target ≤15 min hands-on time)

1. Jira ticket label `onboarding/&lt;first.last&gt;`
2. Okta admin → Directory → People → Add Person
   - First / Last / Primary email = `first.last@lab-&lt;your-handle&gt;.com`
   - Groups: add to `employee` & `engineering` (or `sales`)
3. Automation kicks:
   - Google Workspace SCIM provision → account created, license auto-assigned
   - Slack SCIM provision → user invited to `#general`
4. Reset password & MFA enroll email sent (Okta email template)
5. Verify:
   - User can log in to Google Drive (drive.google.com)
   - User shows “Active” in Slack admin panel
6. Close Jira ticket with comment + timestamp

## Same-Day Off-boarding (Target ≤10 min)

1. Jira ticket label `offboarding/&lt;first.last&gt;`
2. Okta admin → suspend user (immediate)
   - Google Workspace license reclaimed
   - Slack account deactivated
3. Transfer Google Drive files to manager (optional step documented)
4. Wipe MFA factors (Okta → Security → Authenticators)
5. Close ticket, attach Google/Slack audit export PDF

**4. Ticket Simulation:**

**5. Metrics & Evidence:**
