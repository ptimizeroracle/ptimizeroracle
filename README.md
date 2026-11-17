## Atik

I built data platforms, now LLM platforms: gateways, inference routing, serving on Kubernetes, agents on top.

[atiklhy.fr](https://atiklhy.fr/en/) · [writing](https://atiklhy.fr/en/articles/) · [linkedin](https://www.linkedin.com/in/atik-l-0454b0b9) · [email](mailto:contact@binblok.com)

### Mine

- **[Ondine](https://github.com/ptimizeroracle/ondine)**: batch LLM processing for tabular data. Checkpointing, budgets, 100+ providers.

### Merged upstream

- [llm-d-router](https://github.com/llm-d/llm-d-router/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle) (10) and [llm-d](https://github.com/llm-d/llm-d/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle) (4): inference scheduling on Kubernetes
- [AIBrix](https://github.com/vllm-project/aibrix/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle) (2): LLM gateway
- [pandas](https://github.com/pandas-dev/pandas/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [Narwhals](https://github.com/narwhals-dev/narwhals/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle) (4), [ibis](https://github.com/ibis-project/ibis/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle), [Great Expectations](https://github.com/fivetran/great_expectations/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle) (2), [OpenLineage](https://github.com/OpenLineage/OpenLineage/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): dataframes, data quality, lineage
- [Cognee](https://github.com/topoteretes/cognee/pulls?q=is%3Apr+is%3Amerged+author%3Aptimizeroracle): agent memory

### Reported, fixed upstream

Bugs I reported with a reproduction, then fixed by the maintainers: [Polars](https://github.com/pola-rs/polars/issues?q=is%3Aissue+author%3Aptimizeroracle+reason%3Acompleted) (2), [DuckDB](https://github.com/duckdb/duckdb/issues?q=is%3Aissue+author%3Aptimizeroracle+reason%3Acompleted), [SGLang](https://github.com/sgl-project/sglang/issues?q=is%3Aissue+author%3Aptimizeroracle+reason%3Acompleted), [Microsoft Agent Framework](https://github.com/microsoft/agent-framework/issues?q=is%3Aissue+author%3Aptimizeroracle+reason%3Acompleted) (3), [NVIDIA NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay/issues?q=is%3Aissue+author%3Aptimizeroracle+reason%3Acompleted), [vLLM Semantic Router](https://github.com/vllm-project/semantic-router/issues?q=is%3Aissue+author%3Aptimizeroracle+reason%3Acompleted) (3), [AIBrix](https://github.com/vllm-project/aibrix/issues?q=is%3Aissue+author%3Aptimizeroracle+reason%3Acompleted).

### Recent

- [llm-d-router#1598](https://github.com/llm-d/llm-d-router/issues/1598#issuecomment-6884182944), measured: bursty traffic piles onto one pod. On 8 simulated pods I compared 8 pickers under bursts and steady prefix-heavy load. No picker wins both: max-score sends 59 of a 128-request burst to one pod (even is 16), while random pickers spread bursts but copy each prefix to 6-7 pods and pay a cold prefill at p95 (298 ms against 44). [Bench and raw data](https://gist.github.com/ptimizeroracle/889180eb1997e082a81aae8b25d5a78c).
- [vllm#65569](https://github.com/vllm-project/vllm/issues/65569#issuecomment-6627373776), measured: a proposal routes Linear layers to cuBLAS in vLLM's batch-invariant mode, on the claim that cuBLAS is already invariant there. True on every shape I tried but one: the gpt-oss-20b router (32 x 2880) changes bits with batch size, from 29 rows in bf16 and 2 in fp16. Tested on an H200 across every batch size from 1 to 1024; [script and raw data](https://gist.github.com/ptimizeroracle/f0daf044da4624c8d8b70ab506f1249a).
- [llm-d-router#3027](https://github.com/llm-d/llm-d-router/pull/3027), merged: two of the three paths that run metrics extractors had no panic recovery. One buggy extractor could kill the router process on the endpoint path; on the Kubernetes path the panic was swallowed and never counted. Both now recover, count the failure in `datalayer_extract_errors_total` and keep going, like the HTTP path already did.
- [llm-d-router#3379](https://github.com/llm-d/llm-d-router/pull/3379), merged: a pod that had never served a request got no traffic, so it never reported, so it stayed idle. Reproduced on a bench, then confirmed by the reporter on 4 x H100: idle pod in 10 of 12 runs before, 0 of 12 after.
- [aibrix#3297](https://github.com/vllm-project/aibrix/issues/3297), fixed: least-latency routing scored a pod by its lifetime mean, so a pod that slowed down kept winning for a time that grows with its uptime. I measured the lag and derived when the choice flips; the fix now scores the last minute.

I also review others' PRs, usually with a reproduction or a measurement.

### Mostly

- **Data**: where I come from. Spark, Kafka, Databricks, dbt, Polars, and the Hadoop era before that.
- **Inference**: vLLM, SGLang, LiteLLM, Kubernetes. Queueing theory when the numbers stop making sense.
- **Agents**: LangGraph, MCP, evals and tracing. Also Vauban, a reference LLM platform and agent lab I am building as a course: 65 controls, every claim tagged measured or gap. Private for now.

Python, SQL, Go.
