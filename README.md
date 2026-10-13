## Atik

I built data platforms, now LLM platforms: gateways, inference routing, serving on Kubernetes, agents on top.

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

- **Data**: where I come from. Spark, Kafka, Databricks, dbt, Polars, and the Hadoop era before that.
- **Inference**: vLLM, SGLang, LiteLLM, Kubernetes. Queueing theory when the numbers stop making sense.
- **Agents**: LangGraph, MCP, evals and tracing. Also Vauban, a reference LLM platform and agent lab I am building as a course: 65 controls, every claim tagged measured or gap. Private for now.

Python, SQL, Go.
