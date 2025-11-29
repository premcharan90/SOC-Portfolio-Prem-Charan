Incident Title: RDP Brute Force Attack Detected

Date: 28-11-2025

Summary: Multiple failed SSH login attempts were detected targeting the Linux endpoint indicating a brute force attack attempt.

Attack Vector: RDP authentication

Indicators:

- Source IP: 172.16.22x.xxx

- Failed attempts: 15+

Timeline: 

- Initial attempt: 11:54

- Alert triggered: 11:54

Mitigation:

- Attacking IP blocked

- SSH rate-limiting recommended

Recommendations:

- Enable Windows account lockout policy

- Enforce strong passwords

- Enable account lockout
