# Azure DocumentDB samples

Find a sample for managed Azure DocumentDB, with links to its code and evidence.
This repository is a **navigation catalog**, not a code mirror, fork, or
deployment template. Choose between independently maintained standalone samples
and the original [Azure-Samples/documentdb-samples](https://github.com/Azure-Samples/documentdb-samples)
collection; their code, histories, and issue trackers remain in their own repos.

| Start here if you want to… | Go to |
| --- | --- |
| Try vector search in your language without model calls | [Standalone vector search](#standalone-vector-search-and-comparisons) |
| Compare index algorithms and distance metrics | [Standalone comparisons](#standalone-vector-search-and-comparisons) |
| Run a real model-backed hotel recommendation agent | [Standalone agents](#standalone-agents-and-memory) |
| Persist, resume, isolate, and delete agent state | [Agent memory adapters](#standalone-agents-and-memory) |
| Browse the original shared-data sample collection | [Original upstream samples](#original-upstream-samples) |

## Validated standalone samples

**Evidence and public links checked October 12, 2026.** All 13 repositories below
are public under **Azure-DocumentDB**. Clone the selected standalone repository
and follow **its own README**, prerequisites, cost warnings, and explicit write
consent; the whole upstream monorepo is not required for these quickstarts.

The vector, comparison, and hotel-agent repositories are maintained downstream
adaptations of the Microsoft samples, **not replacements for or the canonical
upstream**. Their `UPSTREAM.md` files record the source revision, attribution,
downstream changes, and manual review/porting policy; there is no automatic sync.
The memory repository is a separate adapter project with its own schema contract.

README/repository and `TESTED.md` links below follow current `main`. The dated
validation records identify the exercised implementations and limits; **CI** links
are fixed successful runs at the public `main` heads checked on this date, not
promises about future revisions. CI covers the documented build/test/audit gates;
**it does not rerun the credentialed managed-Azure or paid-model acceptance tests**.
Use `TESTED.md`, rather than saved example output or a CI badge alone,
for live proof.

### Standalone vector search and comparisons

For application developers learning database/index/authentication behavior:
vector samples exercise **IVF, HNSW, and DiskANN**; comparisons exercise those
algorithms across **COS, L2, and IP** (nine combinations). All ten have dated
managed-Azure proof under **native SCRAM and Microsoft Entra OIDC**, using a pinned
**50-record, 1536-dimensional precomputed-vector fixture** and stored-vector query.
These validated paths make **no model calls**. Optional embedding paths in some
repositories are not covered by that proof. Numeric retrieval/index checks are
not semantic-quality or performance benchmarks, nor certification of all tiers.

| Language | Vector search + evidence | Comparisons + evidence |
| --- | --- | --- |
| C# / .NET | [Vector search](https://github.com/Azure-DocumentDB/vector-search-dotnet) · [TESTED](https://github.com/Azure-DocumentDB/vector-search-dotnet/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/vector-search-dotnet/actions/runs/38301312793) | [Compare algorithms](https://github.com/Azure-DocumentDB/select-algorithm-dotnet) · [TESTED](https://github.com/Azure-DocumentDB/select-algorithm-dotnet/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/select-algorithm-dotnet/actions/runs/38306424065) |
| Python | [Vector search](https://github.com/Azure-DocumentDB/vector-search-python) · [TESTED](https://github.com/Azure-DocumentDB/vector-search-python/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/vector-search-python/actions/runs/38306404514) | [Compare algorithms](https://github.com/Azure-DocumentDB/select-algorithm-python) · [TESTED](https://github.com/Azure-DocumentDB/select-algorithm-python/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/select-algorithm-python/actions/runs/38306434679) |
| TypeScript | [Vector search](https://github.com/Azure-DocumentDB/vector-search-typescript) · [TESTED](https://github.com/Azure-DocumentDB/vector-search-typescript/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/vector-search-typescript/actions/runs/38306414424) | [Compare algorithms](https://github.com/Azure-DocumentDB/select-algorithm-typescript) · [TESTED](https://github.com/Azure-DocumentDB/select-algorithm-typescript/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/select-algorithm-typescript/actions/runs/38306445292) |
| Go | [Vector search](https://github.com/Azure-DocumentDB/vector-search-go) · [TESTED](https://github.com/Azure-DocumentDB/vector-search-go/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/vector-search-go/actions/runs/38303041416) | [Compare algorithms](https://github.com/Azure-DocumentDB/select-algorithm-go) · [TESTED](https://github.com/Azure-DocumentDB/select-algorithm-go/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/select-algorithm-go/actions/runs/38303031182) |
| Java | [Vector search](https://github.com/Azure-DocumentDB/vector-search-java) · [TESTED](https://github.com/Azure-DocumentDB/vector-search-java/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/vector-search-java/actions/runs/38306394658) | [Compare algorithms](https://github.com/Azure-DocumentDB/select-algorithm-java) · [TESTED](https://github.com/Azure-DocumentDB/select-algorithm-java/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/select-algorithm-java/actions/runs/38301322512) |

### Standalone agents and memory

| Sample / audience | Purpose | Evidence / CI |
| --- | --- | --- |
| [Go / OpenAI SDK](https://github.com/Azure-DocumentDB/vector-search-agent-go) | Build a planner → vector-search tool → synthesizer agent. | [TESTED](https://github.com/Azure-DocumentDB/vector-search-agent-go/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/vector-search-agent-go/actions/runs/38325177111) |
| [TypeScript / LangChain](https://github.com/Azure-DocumentDB/vector-search-agent-typescript) | Run a model-backed tool-calling hotel recommendation flow. | [TESTED](https://github.com/Azure-DocumentDB/vector-search-agent-typescript/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/vector-search-agent-typescript/actions/runs/38325186281) |
| [Python / LangGraph + TypeScript / AI SDK](https://github.com/Azure-DocumentDB/documentdb-agent-memory) | Persist and resume framework state; exercise scoped memory lifecycle across languages. | [TESTED](https://github.com/Azure-DocumentDB/documentdb-agent-memory/blob/main/TESTED.md) · [CI](https://github.com/Azure-DocumentDB/documentdb-agent-memory/actions/runs/38321122046) |

- **Both hotel agents:** genuine Azure OpenAI fixture/query embeddings, planner
  tool calls, managed-database retrieval, and answer synthesis passed with
  native database/API-key model auth and with Entra database/Entra model auth.
  These were small synthetic **COS/IVF** cases, not mock-only runs. They do not
  certify factuality, prompt-injection resistance, other index algorithms,
  failover, or production readiness. Model calls incur costs; review outputs.
- **Memory adapters:** actual LangGraph framework invocation/resume and AI SDK
  deterministic mock-model persistence, namespace/thread isolation, and complete
  lifecycle tests passed under native and Entra auth. Evidence includes
  **100 simultaneous cold-thread appends per auth mode** and **90 cross-process
  stages total** across both modes, including fresh-process checkpoint resume.
  There were **no live model calls** and no HA/server-crash proof. Quiesce writers
  before deletion; multi-collection delete is not transactional, and retries are
  not an exactly-once guarantee. Application code must authorize scope access.

The managed-database evidence used disposable **M30, single-shard, no-HA**
clusters (MongoDB 8.0 compatibility). Read each validation record for exact
versions, fixtures, topology, safety tests, and exclusions. These are bounded
sample validations, not generic support or production-capacity promises.

## Original upstream samples

The following links retain the original Microsoft sample collection and its
shared-data/infrastructure workflow. **The standalone validation above does not
validate these upstream revisions or transfer downstream fixes upstream.**

### Vector search and algorithm comparisons

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

### Hotel recommendation agents

| Sample | What it demonstrates |
| --- | --- |
| [TypeScript / LangChain](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/vector-search-agent-typescript) | A planner invokes vector search; a synthesizer turns the retrieved hotels into recommendations |
| [Go / OpenAI SDK](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/vector-search-agent-go) | A custom single-turn planner/tool/synthesizer implementation, plus upload and cleanup utilities |

### Before running an upstream sample

Clone the **whole upstream repository** and follow the selected project's README.
Do not copy only a language folder: the examples share
[hotel data and embeddings](https://github.com/Azure-Samples/documentdb-samples/tree/main/ai/data),
[algorithm guidance](https://github.com/Azure-Samples/documentdb-samples/blob/main/ai/includes/choosing-algorithm.md),
and an optional [root infrastructure scaffold](https://github.com/Azure-Samples/documentdb-samples/tree/main/infra).
Some comparison projects require copying the shared vector file into a local
data directory.

At the upstream review snapshot below, these samples required the appropriate
language runtime, an Azure DocumentDB cluster, Azure OpenAI deployments, and
configured authentication/network access. Even examples using precomputed
document vectors generated query embeddings through Azure OpenAI. Recheck the
selected upstream README for changes; these prerequisites do not apply to
every standalone sample above.

- Review cloud costs, region/model availability, quotas, authentication, and
  supported API versions before provisioning. Some configuration uses preview
  API versions; sample READMEs differ on model names and minimum cluster tiers.
- Review infrastructure before using `azd`: the reviewed source included broad
  public-network defaults, database administrator roles, and a fallback
  administrator password. Provisioning needs deliberate configuration.
- Use a disposable sample database. Index/data loaders and comparison or cleanup
  commands can drop collections or indexes.
- Build/syntax CI and saved example output do not establish successful live
  deployment. This catalog itself does not execute or certify sample code; the
  standalone section links separately recorded, scoped live evidence.

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

Report standalone code problems to the selected **standalone repository's issue
tracker** and follow its contribution/provenance guidance. For original upstream
code, use the [upstream issue tracker](https://github.com/Azure-Samples/documentdb-samples/issues)
and [upstream contribution guide](https://github.com/Azure-Samples/documentdb-samples/blob/main/CONTRIBUTING.md).
Catalog corrections belong here; no sample code is duplicated in this catalog.
Porting fixes between downstream and upstream requires a separate, reviewed
change in the appropriate repository.

The source samples are **Copyright (c) Microsoft Corporation**, under the
[MIT license](https://github.com/Azure-Samples/documentdb-samples/blob/main/LICENSE.md).
Retain applicable copyright, license, and data notices when reusing material.
This catalog does not relicense the samples or datasets.

Original upstream content review: **September 30, 2026**, against upstream revision
[`f5a2675`](https://github.com/Azure-Samples/documentdb-samples/commit/f5a2675bbf349737234d0391e3ebee24b260e06f).
Those sample links follow upstream `main`; use the reviewed revision for a fixed
snapshot. Standalone discovery and evidence links were checked **October 12, 2026**;
this does not imply a new upstream code review. Catalog updates and downstream
source synchronization are manual; no code mirror or scheduled automation is used.
