# SOC Incident Report — INV-001

## 1. Incident Overview

| Field | Details |
|---|---|
| Incident ID | INV-001 |
| Incident Type | Phishing / Suspected Account Compromise |
| Severity | HIGH |
| Status | Contained / Under Investigation |
| Affected User | employee@company.local |
| Primary IOC | microsoft-security-verification.com |
| Suspicious IP | 185.234.72.91 |

---

## 2. Executive Summary

A phishing email containing a suspicious external link was
delivered to the affected user.

The user clicked the link. Subsequent investigation identified
multiple failed authentication attempts followed by a successful
login from an unfamiliar IP address and device.

Further investigation identified unauthorized mailbox access and
creation of an external email forwarding rule. An email containing
financial information was also accessed.

No malware execution was detected on the endpoint.

Based on the correlated evidence, the incident is classified as a
HIGH-severity likely account compromise with potential
sensitive-information exposure.

---

## 3. Investigation Timeline

| Time | Event |
|---|---|
| 10:27:42 | User clicked phishing URL |
| 10:27:45 | Browser attempted connection to suspicious domain |
| 10:27:47 | No file download detected |
| 10:28:02 | No suspicious process execution detected |
| 10:31:44 | Failed login from unfamiliar IP |
| 10:32:01 | Second failed login from unfamiliar IP |
| 10:32:19 | Successful login from 185.234.72.91 |
| 10:33:07 | Mailbox access detected |
| 10:33:41 | External forwarding rule created |
| 10:34:03 | Three emails accessed |
| 10:34:28 | Financial-information email accessed |
| 10:35:10 | Unauthorized forwarding rule removed |

---

## 4. Indicators of Compromise

### Suspicious Domain

`microsoft-security-verification.com`

### Suspicious IP

`185.234.72.91`

### External Forwarding Destination

`external-mail@example.net`

---

## 5. Endpoint Investigation

### Device

`WIN-CLIENT-014`

### Browser

`Microsoft Edge`

### Findings

- No file download detected.
- No suspicious process execution detected.
- Browser session ended normally.

### Assessment

No malware execution was detected on the endpoint.

The available evidence does not support classifying this incident
as a confirmed malware infection.

---

## 6. Authentication Investigation

The affected account experienced multiple failed authentication
attempts followed by a successful authentication from an
unfamiliar IP address.

### Findings

- Source IP: `185.234.72.91`
- Device: Unknown
- Location: Unknown
- No successful login from this IP during the previous 30 days.
- Successful authentication occurred shortly after the phishing
  link was clicked.

### Assessment

The authentication pattern is consistent with potential
unauthorized account access.

---

## 7. Mailbox Investigation

### Findings

- Unauthorized mailbox access detected.
- External forwarding rule created.
- Three emails marked as read.
- One email containing financial information accessed.
- No emails sent from the account.
- Unauthorized forwarding rule removed.

### Potential Impact

Potential exposure of sensitive information and unauthorized
mailbox access.

There is currently insufficient evidence to confirm that the
financial information was successfully exfiltrated.

---

## 8. Containment Actions

The following containment actions were initiated:

- Account protection initiated.
- Suspicious sessions/tokens identified for revocation.
- Password reset required.
- MFA status verified.
- Unauthorized forwarding rule removed.
- Mailbox activity reviewed.
- Suspicious IP escalated for further investigation.
- Organization-wide search recommended for related indicators.

---

## 9. Severity Assessment

### Severity: HIGH

### Justification

The incident contains multiple correlated indicators:

1. Confirmed phishing activity.
2. User interaction with the phishing URL.
3. Suspicious authentication attempts.
4. Successful authentication from an unfamiliar IP/device.
5. Unauthorized mailbox access.
6. Creation of an external forwarding rule.
7. Access to financial information.

Together, these findings strongly indicate a likely account
compromise and create a credible risk of sensitive-information
exposure.

---

## 10. Recommendations

### Immediate

- Complete account containment.
- Reset affected credentials.
- Revoke suspicious sessions and tokens.
- Verify MFA.
- Remove any remaining unauthorized mailbox rules.
- Continue monitoring the affected account.

### Investigation

- Investigate IP `185.234.72.91`.
- Search SIEM logs for the same IP.
- Search for the suspicious domain across the organization.
- Search for the external forwarding destination.
- Review additional mailbox activity.
- Determine whether sensitive information was actually
  exfiltrated.

### Preventive

- Strengthen phishing awareness training.
- Review email security controls.
- Monitor external forwarding-rule creation.
- Implement alerts for anomalous authentication.
- Review conditional-access policies where applicable.

---

## 11. Final SOC Conclusion

The investigation began as a phishing alert and developed into
a likely account-compromise incident.

No malware execution was detected on the affected endpoint.
However, authentication and mailbox evidence indicates
unauthorized account activity.

The incident is classified as HIGH severity because of the
combination of suspicious authentication, unauthorized mailbox
access, external forwarding, and potential exposure of financial
information.

Further investigation is required to determine the full scope
and whether sensitive information was exfiltrated.

---

## 12. Evidence References

- `Evidence/endpoint-activity.txt`
- `Evidence/authentication-activity.txt`
- `Evidence/suspicious-ip-analysis.txt`
- `Evidence/mailbox-activity.txt`
- `Evidence/containment-actions.txt`
- `Investigation/investigation-notes.txt`

---

## Disclaimer

This is a simulated cybersecurity investigation created for
educational and portfolio purposes.

All users, domains, IP addresses, email addresses, and security
events in this project are simulated.
