# Sigma Detection Rules

> Status: Planning

A portfolio collection of original, tested Sigma rules for defensive detection engineering. Each rule will include its required telemetry, ATT&CK mapping, test evidence, false-positive analysis, and tuning guidance.

## Goals

- Learn the Sigma rule specification and write portable detections.
- Build rules from observed lab telemetry rather than copying existing content.
- Map detections to MITRE ATT&CK only when the tested behavior supports the mapping.
- Document log-source requirements, investigation steps, and operational limitations.
- Validate syntax and behavior through repeatable tests.

## Initial rule roadmap

| Rule idea | Planned log source | Detection focus |
|---|---|---|
| Repeated failed logons | Windows authentication | Password guessing indicators |
| New privileged local account | Windows account management | Unexpected privilege creation |
| Suspicious PowerShell command line | PowerShell/process creation | Encoded or unusual execution |
| Scheduled task creation | Windows task/process events | Persistence behavior |
| Unexpected service installation | Windows system events | Service-based persistence |
| Security audit log cleared | Windows audit events | Defense evasion |
| SSH brute-force pattern | Linux authentication | Repeated remote failures |
| New sudo-capable account | Linux account/configuration logs | Privilege escalation risk |
| Suspicious shell download behavior | Linux process/audit logs | Unusual command execution |
| Unexpected administrative tool execution | Endpoint process logs | Dual-use tool monitoring |

Rule names and ATT&CK tags will be finalized after implementation and testing.

## Planned repository structure

```text
.
├── README.md
├── rules/
│   ├── windows/
│   │   ├── process_creation/
│   │   ├── account_management/
│   │   └── system/
│   └── linux/
│       ├── process_creation/
│       └── authentication/
├── tests/
│   ├── positive/
│   ├── negative/
│   └── test-cases/
├── docs/
│   ├── rule-writing-standard.md
│   ├── testing-methodology.md
│   └── coverage-matrix.md
└── sample-logs/
```

## Rule quality standard

Every completed rule will include:

- Unique rule identifier
- Clear title and description
- Author and creation date
- Specific log source
- Detection selection and condition
- Appropriate severity level
- Supported ATT&CK tags
- References
- Known false positives
- Data-source prerequisites
- Test procedure and expected result
- Tuning and investigation notes

## Example rule workflow

1. Define the behavior to detect.
2. Generate the behavior safely in the isolated lab.
3. Confirm the expected events and fields are present.
4. Write the smallest reliable Sigma condition.
5. Validate the YAML and Sigma schema.
6. Test against positive and negative samples.
7. Convert the rule to a target query format when appropriate.
8. Document false positives and tuning.
9. Save sanitized test evidence.
10. Review the ATT&CK mapping and severity.

## Milestones

- [ ] Document naming, severity, and rule-quality conventions.
- [ ] Configure automated Sigma validation.
- [ ] Create reusable positive and negative test-case templates.
- [ ] Complete five Windows rules.
- [ ] Complete three Linux rules.
- [ ] Add false-positive samples and tuning notes.
- [ ] Generate an ATT&CK coverage matrix.
- [ ] Convert selected rules to a SIEM query format and compare results.
- [ ] Publish testing lessons and limitations.
- [ ] Prepare one original, production-quality rule for possible upstream contribution.

## Validation plan

Rules will be checked for:

- Valid YAML and Sigma syntax
- Required metadata
- Expected matches against positive test data
- No matches against known negative samples
- Accurate log-source declaration
- Supported ATT&CK mapping
- Clear false-positive documentation

## Safety and originality

Rules and samples will be created from personally owned, isolated lab systems. This repository will not contain employer or customer logs, credentials, personal information, malicious payloads, or copied community rules presented as original work.

## References

- [Sigma documentation](https://sigmahq.io/docs/)
- [Sigma rule specification](https://sigmahq.io/sigma-specification/specification/sigma-rules-specification.html)
- [MITRE ATT&CK](https://attack.mitre.org/)
