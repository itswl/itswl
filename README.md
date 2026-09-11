**SRE / platform engineering → agent infrastructure.** Shenzhen.

I build alerting systems, and the rails that let AI agents touch production without being trusted.

---

### [WebhookWise](https://github.com/itswl/WebhookWise) · self-hosted alert intelligence

Sits between your monitoring and your chat: dedup, AI triage, and a decision trace. *"Why didn't I get paged?"* gets an answer, not a guess.

It also caught itself being wrong. One week it filed **90% of alerts as `high`**; an agentic investigator scored the same alerts and **agreed with 26%**. Measuring that dropped 59% of weekly volume out of `high`. The script still refuses to downgrade a rule the investigator called high more than a third of the time — that noise needs a more specific alert, not a mute.

That is [the first thing in the README](https://github.com/itswl/WebhookWise#the-problem-it-turned-out-to-have), ahead of the feature list. → [How the calibration works](https://blog.wetalk.eu.org/ops/services/severity-calibration/) (中文)

### [hookstack](https://github.com/itswl/hookstack) · agents on production, without being trusted

Three services; **hookprobe** runs one read-only agent per investigation. Read-only is *constructed*, not promised — scoped credentials, a bash guard, a disposable container.

The part I hadn't seen elsewhere is the input guard: **an agent cannot write what steers its next run.** One injected line in a runbook would otherwise outlive the run that read it. → [Read-only by construction](https://blog.wetalk.eu.org/ops/services/read-only-by-construction-en/) (English · [中文](https://blog.wetalk.eu.org/ops/services/read-only-by-construction/))

---

### Measured, not claimed

- **Two alert systems, same production traffic, two days.** 88.6% agreement across 35 comparable judgments. All four disagreements traced to one bug: recovery semantics lost across three system boundaries. → [Data and method](https://blog.wetalk.eu.org/ops/services/shadow-run-two-alert-systems/) (中文)
- **13 PRs merged into [easzlab/kubeasz](https://github.com/easzlab/kubeasz)** (11k ★) — etcd backup paths, nodelocaldns upstream DNS, apiserver health checks behind ex-lb, harbor port probing.

