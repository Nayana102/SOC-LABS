 🛡️ SOC Analyst Triage Playbook or Template
Standardized Operating Procedure for Alert Investigation

This playbook outlines the 5-step investigative logic I follow for every security alert to ensure accurate detection and rapid response.

### *1. Identify Context*
- Determine the 'Who, Where, and When.'
- Compare activity against the user's established baseline (working hours, typical locations).

### *2. Collect Evidence (Enrichment)*
- *Internal Logs:* Review SIEM (Wazuh/Splunk) and system logs (auth.log, access.log) {for other activitives with same use ID , IP address}.
- *External Intel:* Use AbuseIPDB, VirusTotal, and URLScan.io to verify IP/Domain reputation and overview.

### *3. Validate the Alert*
- *True Positive (TP):* Malicious intent confirmed (e.g., automated brute force, known malicious payload).
- *False Positive (FP):* Benign activity identified (e.g., authorized admin testing, user password mistake).

### *4. Assign Severity*
- *Low/Medium:* Probing attempts, unsuccessful scans, or contained activity.
- *High/Critical:* Successful unauthorized access, malware execution, or targeting of sensitive (Finance/Admin) assets.

### *5. Action & Escalation*
- Remediate via IP shunning or account lockout.
- Escalate to L2 with technical logs and a "Disposition" summary.
