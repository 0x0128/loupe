# 🔴 Loupe · Home SOC Lab

> *Loupe*: a jeweler's magnifier — the lens you use to examine every detail.

A **miniature SOC** built from scratch to practice the full detection-and-response cycle.
I simulate attacks in a controlled, isolated lab and learn to **detect, investigate and document**
them the way an N2 analyst would.

## What it demonstrates
- Building telemetry from zero: **Windows VM + Sysmon + SIEM**.
- Simulating **MITRE ATT&CK** techniques in a controlled way and finding them in the logs.
- **Detection-as-code**: versioned **Sigma** rules, each with its test and validated in CI.
- A **full investigation** of a chained attack, with its report and runbooks.
- Measuring **ATT&CK coverage** honestly: what I detect and what I don't.

## Architecture

```
[ Windows VM + Sysmon ]  --logs-->  [ Agent ]  -->  [ SIEM: Elastic / Wazuh ]
         |                                                  |
   Atomic Red Team                                   Sigma rules (CI)
   (simulated attacks)                               Dashboard
                                                     Investigation + report
```
Everything runs on an **isolated** (host-only) network, on a personal machine. Never in a real environment.

## Structure

| Folder | What it holds |
|---|---|
| [`lab/`](./lab) | How to build it: VM, Sysmon and SIEM. Reproducible, no credentials. |
| [`attacks/`](./attacks) | One card per technique: which test, which event reveals it, and a screenshot. |
| [`detections/`](./detections) | Sigma rules with their test and their KQL / Elastic version. |
| [`tools/`](./tools) | Python triage scripts. |
| [`runbooks/`](./runbooks) | What the analyst does for each alert. |
| [`reports/`](./reports) | Incident and purple-team reports. |

## Roadmap (v1)

- [ ] **Sprint 1** — Lab built and verified
- [ ] **Sprint 2** — 5 techniques simulated and detected
- [ ] **Sprint 3** — Sigma rules + CI pipeline
- [ ] **Sprint 4** — Full investigation + report + runbooks
- [ ] **Sprint 5** — Dashboard, coverage, final README and video

## ⚠️ Lab safety
Everything happens in **isolated virtual machines** on a personal computer — never on a work laptop
or any company network. Snapshot before every test. **No** real malware is used, and nothing
sensitive is committed (raw logs, memory dumps, samples): see the [`.gitignore`](./.gitignore).

---

<sub>Built by [@0x0128](https://github.com/0x0128) · part of my cybersecurity portfolio.</sub>
