## Atik

I build and run LLM platforms: gateways, inference routing, serving on Kubernetes, agents on top.
When something I run misbehaves, I reproduce it, measure it, and send the fix upstream.

[atiklhy.fr](https://atiklhy.fr/en/) · [writing](https://atiklhy.fr/en/articles/) · [linkedin](https://www.linkedin.com/in/atik-l-0454b0b9) · [email](mailto:contact@binblok.com)

### Mine

- **[Ondine](https://github.com/ptimizeroracle/ondine)**: batch LLM processing for tabular data. Checkpointing, budgets, 100+ providers.

### Merged upstream

- [llm-d-router](https://github.com/llm-d/llm-d-router/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle) and [llm-d](https://github.com/llm-d/llm-d/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): inference scheduling on Kubernetes
- [AIBrix](https://github.com/vllm-project/aibrix/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): LLM gateway
- [Narwhals](https://github.com/narwhals-dev/narwhals/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [Great Expectations](https://github.com/fivetran/great_expectations/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [Cognee](https://github.com/topoteretes/cognee/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [OpenLineage](https://github.com/OpenLineage/OpenLineage/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): data and agent memory

### In review

- [llm-d-router#3379](https://github.com/llm-d/llm-d-router/pull/3379): a pod that had never served a request got no traffic, so it never reported, so it stayed idle. Reproduced on a bench, then confirmed by the reporter on 4 x H100: idle pod in 10 of 12 runs before, 0 of 12 after.

### Mostly

Python and Go. vLLM, Kubernetes, Envoy, LangGraph. Queueing theory when the numbers stop making sense.
