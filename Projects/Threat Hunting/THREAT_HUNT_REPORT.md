Threat Hunting Report – Suspicious Endpoint Behaviour

Date: 29-11-2025

Hypothesis: An attacker may attempt to execute obfuscated PowerShell commands and execute binaries from temporary directories.

Investigation Process:

- Monitored Sysmon telemetry

- Filtered suspicious process executions

- Analysed command-line arguments

Findings:

- Encoded PowerShell execution observed

- Execution of binary from Temp directory

- Unusual parent-child process relationships

- Conclusion: The activity matched known TTPs associated with malware execution and post-exploitation.

MITRE Mapping:

- T1059.001 – PowerShell

- T1204 – User Execution

Recommendations:

-Block PowerShell encoded commands

- Restrict execution from Temp directory

- Monitor suspicious parent processes
