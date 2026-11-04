## Atik

I built data platforms, now LLM platforms: gateways, inference routing, serving on Kubernetes, agents on top.

[atiklhy.fr](https://atiklhy.fr/en/) · [writing](https://atiklhy.fr/en/articles/) · [linkedin](https://www.linkedin.com/in/atik-l-0454b0b9) · [email](mailto:contact@binblok.com)

### Mine

- **[Ondine](https://github.com/ptimizeroracle/ondine)**: batch LLM processing for tabular data. Checkpointing, budgets, 100+ providers.

### Merged upstream

- [llm-d-router](https://github.com/llm-d/llm-d-router/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle) and [llm-d](https://github.com/llm-d/llm-d/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): inference scheduling on Kubernetes
- [AIBrix](https://github.com/vllm-project/aibrix/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): LLM gateway
- [Narwhals](https://github.com/narwhals-dev/narwhals/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [Great Expectations](https://github.com/fivetran/great_expectations/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [Cognee](https://github.com/topoteretes/cognee/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [OpenLineage](https://github.com/OpenLineage/OpenLineage/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): data and agent memory

### Recent

- [vllm#65569](https://github.com/vllm-project/vllm/issues/65569#issuecomment-6627373776), measured: a proposal routes Linear layers to cuBLAS in vLLM's batch-invariant mode, on the claim that cuBLAS is already invariant there. True on every shape I tried but one: the gpt-oss-20b router (32 x 2880) changes bits with batch size, from 29 rows in bf16 and 2 in fp16. Tested on an H200 across every batch size from 1 to 1024; [script and raw data](https://gist.github.com/ptimizeroracle/f0daf044da4624c8d8b70ab506f1249a).
- [LocalAI#12992](https://github.com/mudler/LocalAI/issues/12992), fixed: federated load balancing recorded a request only after the connection was open, so a burst of requests all saw the same idle node and went to it. Reported with a reproduction; fixed upstream.
- [llm-d-router#3379](https://github.com/llm-d/llm-d-router/pull/3379), merged: a pod that had never served a request got no traffic, so it never reported, so it stayed idle. Reproduced on a bench, then confirmed by the reporter on 4 x H100: idle pod in 10 of 12 runs before, 0 of 12 after.
- [aibrix#3297](https://github.com/vllm-project/aibrix/issues/3297), fixed: least-latency routing scored a pod by its lifetime mean, so a pod that slowed down kept winning for a time that grows with its uptime. I measured the lag and derived when the choice flips; the fix now scores the last minute.
- [llm-d-router#3814](https://github.com/llm-d/llm-d-router/pull/3814), merged: the chart cut release and namespace to 40 characters each, so two namespaces with the same prefix got one cluster-wide RBAC name, and long names rendered invalid YAML. It was why a llm-d nightly failed. Now unique, with a regression test in the chart checks.

### Mostly

- **Data**: where I come from. Spark, Kafka, Databricks, dbt, Polars, and the Hadoop era before that.
- **Inference**: vLLM, SGLang, LiteLLM, Kubernetes. Queueing theory when the numbers stop making sense.
- **Agents**: LangGraph, MCP, evals and tracing. Also Vauban, a reference LLM platform and agent lab I am building as a course: 65 controls, every claim tagged measured or gap. Private for now.

Python, SQL, Go.
