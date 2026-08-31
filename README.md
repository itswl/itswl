### SRE / platform engineering → AI infra. Shenzhen.

I build alerting infrastructure, and the rails that let AI agents touch
production without being trusted.

**[WebhookWise](https://github.com/itswl/WebhookWise)** — self-hosted alert intelligence between your monitoring and your chat.
It filed **90% of a week's alerts as `high`; an independent agentic investigator agreed with 26%** of them.
Measuring that, downgrading 59% of weekly volume, and refusing the over-correction is
[the first thing in the README](https://github.com/itswl/WebhookWise#the-problem-it-turned-out-to-have).

**[hookstack](https://github.com/itswl/hookstack)** — three services that split alert handling; **hookprobe** runs one read-only agent per investigation.
Read-only is constructed, not promised: scoped credentials, a bash guard, a disposable container, and an input
guard so **the agent cannot write what steers its next run** — one injected line in a runbook would otherwise
outlive the run that read it. ([写透这件事的文章](https://blog.wetalk.eu.org/ops/services/read-only-by-construction/))

**Shadow-run, measured** — two alert systems judging the same production traffic for two days:
**88.6% agreement across 35 comparable judgments**, and all four disagreements traced to a single bug —
recovery semantics lost across three system boundaries. ([数据和过程](https://blog.wetalk.eu.org/ops/services/shadow-run-two-alert-systems/))

**GPU training clusters** — InfiniBand, NCCL-tests, XID/DCGM monitoring.
([三板斧笔记](https://blog.wetalk.eu.org/ops/services/gpu-cluster-ib-nccl-xid/))

---

📝 141 posts since 2018, mostly 中文 → **[blog.wetalk.eu.org](https://blog.wetalk.eu.org)**
· project pages: [WebhookWise](https://itswl.github.io/WebhookWise/) / [hookstack](https://itswl.github.io/hookstack/)
· 📫 imwl@live.com
