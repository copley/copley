# Max Copley

Senior software engineer and systems engineer based in Wellington, New Zealand.

I specialize in difficult software failures: JVM/runtime behavior, networking,
backpressure, concurrency, production debugging, cloud infrastructure, CI/CD,
and system reliability.

My current focus is AI-assisted systems engineering: using advanced models as
an engineering harness for reproduction, root-cause analysis, implementation,
adversarial testing, and verification.

## Current flagship work

### Netty #17304 — TLS backpressure / direct-memory regression

Upstream PR: netty/netty#17391

Investigated a pooled direct-memory regression affecting HTTPS workloads with
slow consumers. Isolated the backpressure failure to SslHandler, implemented a
bounded TLS wrapping mechanism, added a regression test, and validated the
repair against the complete Netty handler module:

- 15,635 tests
- 0 failures
- 0 errors
- JDK TLS compatibility verified
- BoringSSL/OpenSSL compatibility verified

### AI Engineering Harness

[copley-ai-engineering-harness](...)

A model-independent engineering control plane for directing AI systems through:

reproduction → evidence → root cause → design → implementation → verification

The objective is not code generation. It is reliable AI-assisted systems
engineering with persistent state, evidence gates and human approval.

### Paid Debugging Lab

[paid-debugging-lab](...)

Public case studies demonstrating production-style debugging, CI repair,
environment diagnosis and repository rescue.
