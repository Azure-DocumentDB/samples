# Azure DocumentDB samples

Find the existing Azure DocumentDB samples without maintaining another copy.
The code, development history, and code-issue tracker remain in
**[Azure-Samples/documentdb-samples](https://github.com/Azure-Samples/documentdb-samples)**.
This repository is a navigation catalog, not a fork or deployment template.

## Vector search and algorithm comparisons

The vector-search projects demonstrate hotel embeddings and IVF, HNSW, and
DiskANN indexes. The comparison projects run the three algorithms against
cosine, L2, and inner-product metrics: nine combinations. These are educational
examples, not production-scale performance benchmarks.

| Language | Vector search | Algorithm comparison |
| --- | --- | --- |
| C# / .NET | [Vector search](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/vector-search-dotnet) | [Compare algorithms](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/select-algorithm-dotnet) |
| Python | [Vector search](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/vector-search-python) | [Compare algorithms](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/select-algorithm-python) |
| TypeScript | [Vector search](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/vector-search-typescript) | [Compare algorithms](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/select-algorithm-typescript) |
| Go | [Vector search](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/vector-search-go) | [Compare algorithms](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/select-algorithm-go) |
| Java | [Vector search](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/vector-search-java) | [Compare algorithms](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/select-algorithm-java) |

## Hotel recommendation agents

| Sample | What it demonstrates |
| --- | --- |
| [TypeScript / LangChain](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/vector-search-agent-typescript) | A planner invokes vector search; a synthesizer turns the retrieved hotels into recommendations |
| [Go / OpenAI SDK](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/vector-search-agent-go) | A custom single-turn planner/tool/synthesizer implementation, plus upload and cleanup utilities |

## Before running a sample

Clone the **whole upstream repository** and follow the selected project's README.
Do not copy only a language folder: the examples share
[hotel data and embeddings](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/data),
[algorithm guidance](https://github.com/Azure-Samples/documentdb-samples/blob/main/ai/includes/choosing-algorithm.md),
and an optional [root infrastructure scaffold](https://github.com/Azure-Samples/documentdb-samples/tree/main/infra).
Some comparison projects require copying the shared vector file into a local
data directory.

These are samples, not production services. They require the appropriate
language runtime, an Azure DocumentDB cluster, Azure OpenAI deployments, and
configured identity/network access. Even examples using precomputed document
vectors generate query embeddings through Azure OpenAI.

- Review cloud costs, region/model availability, quotas, authentication, and
  supported API versions before provisioning. Some configuration uses preview
  API versions; sample READMEs differ on model names and minimum cluster tiers.
- Review infrastructure before using `azd`: current source includes broad
  public-network defaults, database administrator roles, and a fallback
  administrator password. Provisioning needs deliberate configuration.
- Use a disposable sample database. Index/data loaders and comparison or cleanup
  commands can drop collections or indexes.
- Build/syntax CI and saved example output do not establish successful live
  deployment. This catalog does not run or certify the samples.

For current service guidance, see
[Azure DocumentDB documentation](https://learn.microsoft.com/azure/documentdb/)
and [Azure OpenAI documentation](https://learn.microsoft.com/azure/ai-services/openai/).

## Related open-source DocumentDB examples

These projects target the open-source DocumentDB engine and may use local
Docker or other environments. Follow their own prerequisites rather than
assuming the managed Azure setup is interchangeable.

- [DocumentDB samples gallery](https://github.com/documentdb/documentdb-samples-gallery):
  application examples and the existing sample registry.
- [DocumentDB playground](https://github.com/documentdb/documentdb-playground):
  driver/ODM compatibility playgrounds and related local experiments.

## Contributions and provenance

Report sample-code problems to the
[upstream issue tracker](https://github.com/Azure-Samples/documentdb-samples/issues)
and follow the
[upstream contribution guide](https://github.com/Azure-Samples/documentdb-samples/blob/main/CONTRIBUTING.md).
Catalog corrections belong in this repository; code fixes belong upstream.

The source samples are **Copyright (c) Microsoft Corporation**, under the
[MIT license](https://github.com/Azure-Samples/documentdb-samples/blob/main/LICENSE.md).
Retain applicable copyright, license, and data notices when reusing material.
This catalog does not relicense the samples or datasets.

Catalog last checked: **September 30, 2026**, against upstream revision
[`f5a2675`](https://github.com/Azure-Samples/documentdb-samples/commit/f5a2675bbf349737234d0391e3ebee24b260e06f).
The sample links follow upstream `main`; use the reviewed revision for a fixed
snapshot. Catalog updates are manual; no code mirror or scheduled automation
is needed.
