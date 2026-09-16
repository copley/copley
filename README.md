# Max Copley

Software engineer based in Wellington, New Zealand, focused on **production debugging, backend systems, developer tooling, CI/CD reliability, and AI-assisted systems engineering**.

I am most useful when a failure is ambiguous, intermittent, crosses multiple layers, or needs stronger evidence than "the patch seems to work". My engineering process is built around reproducibility, root-cause isolation, bounded fixes, and regression verification.

## What I work on

- Java / JVM backend and infrastructure debugging
- TypeScript and Python runtime failures
- concurrency, lifecycle, cache, transport, and resource-ownership bugs
- GitHub Actions, Docker, AWS, Gradle, Playwright, Vitest, and API integrations
- production-style incident reproduction and regression testing
- AI-assisted engineering workflows with explicit evidence gates

## Proof of work

### Paid Debugging Lab

[**copley/paid-debugging-lab**](https://github.com/copley/paid-debugging-lab) is my public debugging storefront and case-study archive. It documents investigations across CI lifecycle failures, concurrency, authentication propagation, serialization, runtime compatibility, browser automation, AWS/CDK, Docker/Buildx, GitHub Actions, pytest/Pydantic, Vitest, Wrangler/Miniflare, and related systems work.

### Upstream contribution in review

[**vitest-dev/vitest#11155**](https://github.com/vitest-dev/vitest/pull/11155) fixes a Vitest 5 benchmark project-filter identity regression. The contribution includes reproduction, a bounded TypeScript change, regression coverage for selection/exclusion behaviour, and broad verification. It is currently **in review**, not presented as merged work.

### Current source-inspected debugging queue

_Last reviewed: 2026-09-16._ These are active investigations, not claims of contribution:

- [**vitest-dev/vitest#11276**](https://github.com/vitest-dev/vitest/issues/11276) — browser mode intentionally constructs `interceptorPlugin({ registerWebSocketEvents: false })`, but the plugin still exposes a `configureServer` hook whose body merely returns. Vite 8 detects the forbidden environment hook from the plugin shape before that guard can help; omitting the hook entirely in the disabled case is a small, regression-testable fix.
- [**vitest-dev/vitest#11281**](https://github.com/vitest-dev/vitest/issues/11281) — project-specific `defineCacheKeyGenerator` callbacks are registered into one workspace-global generator set, then every generator runs for every environment. Two projects can therefore contribute the same combined cache-key material to a shared module even though their transforms differ.
- [**actions/runner#4723**](https://github.com/actions/runner/issues/4723) — the runner's workflow-permissions model is stale beyond the JSON schema: `code-quality` and `copilot-requests` are absent from the schema, the `Permissions` data model/comparison map, and conversion switch, so synchronization with the GitHub-owned language-services schema needs to cover parsing and policy semantics rather than a one-line schema edit.

The queue is deliberately source-inspected before any public diagnosis is posted. The next useful artifact should be a reproducer, regression test, or bounded patch—not an ownership-only comment.

### AI Engineering Harness

[**copley/copley-ai-engineering-harness**](https://github.com/copley/copley-ai-engineering-harness) is a model-independent control plane for directing AI systems through a deterministic engineering lifecycle:

```text
DISCOVERY
→ REPRODUCTION
→ EVIDENCE
→ ROOT CAUSE
→ DESIGN
→ IMPLEMENTATION
→ REGRESSION TESTING
→ STRESS / INTEGRATION TESTING
→ REVIEW
→ VERIFIED RESULT
```

The objective is not code generation by itself. It is **reliable AI-assisted systems engineering with reproducible evidence, adversarial review, and human approval**.

## Selected systems investigation

### Netty TLS backpressure / direct-memory regression

[**netty/netty#17391**](https://github.com/netty/netty/pull/17391) investigates bounded TLS wrapping and backpressure behaviour in `SslHandler` under slow-consumer conditions. The work focuses on queue ownership, writability semantics, direct-memory pressure, and regression coverage rather than a broad behavioural rewrite.

## How I debug

```text
Issue discovery
→ repository and environment setup
→ codebase mapping
→ deterministic reproduction
→ instrumentation and evidence capture
→ hypothesis testing
→ root-cause isolation
→ smallest safe patch
→ regression / stress / integration tests
→ adversarial review
→ upstream PR or production-ready incident package
```

A useful debugging engagement should leave behind a result another engineer can independently verify: the reproduction, the failure boundary, the root cause, the patch, and the test that prevents recurrence.

## Paid debugging

For a focused repository failure, CI breakage, runtime bug, or difficult integration problem, start at [**paid-debugging-lab**](https://github.com/copley/paid-debugging-lab). Good requests have one repository, one concrete failing behaviour, logs or a reproduction, and a clear expected outcome.
