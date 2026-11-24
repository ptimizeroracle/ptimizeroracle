## Atik

I built data platforms, now agentic platforms. Focus: software factories as a service, agent permissions, retrieval, proactive actions, and human-in-the-loop orchestration.

[atiklhy.fr](https://atiklhy.fr/en/) · [writing](https://atiklhy.fr/en/articles/) · [linkedin](https://www.linkedin.com/in/atik-l-0454b0b9) · [email](mailto:contact@binblok.com)

### Mine

- **[Ondine](https://github.com/ptimizeroracle/ondine)**: batch LLM processing for tabular data. Checkpointing, budgets, 100+ providers.

### Upstream

- [llm-d-router](https://github.com/llm-d/llm-d-router/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle) and [llm-d](https://github.com/llm-d/llm-d/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): inference scheduling on Kubernetes
- [AIBrix](https://github.com/vllm-project/aibrix/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): LLM gateway
- [Narwhals](https://github.com/narwhals-dev/narwhals/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [pandas](https://github.com/pandas-dev/pandas/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [ibis](https://github.com/ibis-project/ibis/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [Great Expectations](https://github.com/fivetran/great_expectations/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [OpenLineage](https://github.com/OpenLineage/OpenLineage/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): dataframes, data quality, lineage

### A few I liked

- [llm-d-router#3379](https://github.com/llm-d/llm-d-router/pull/3379): a pod that had never served a request got no traffic, so it never reported, so it stayed idle. Reproduced on a bench, then confirmed by the reporter on 4 x H100.
- [llm-d-router#1598](https://github.com/llm-d/llm-d-router/issues/1598#issuecomment-6884182944): compared 8 pickers under bursty and prefix-heavy load. None wins both. [Bench and data](https://gist.github.com/ptimizeroracle/889180eb1997e082a81aae8b25d5a78c).
- [aibrix#3297](https://github.com/vllm-project/aibrix/issues/3297): least-latency routing scored a pod by its lifetime mean, so a pod that slowed down kept winning. The fix now scores the last minute.

### Mostly

- **Data**: where I come from. Spark, Kafka, Databricks, dbt, Polars.
- **Inference**: vLLM, LiteLLM, Kubernetes. Queueing theory when the numbers stop making sense.
- **Agents**: LangGraph, MCP, evals and tracing. Also Vauban, a reference architecture for LLM and agent platforms in regulated environments. Private for now.

Python, SQL, Go.
