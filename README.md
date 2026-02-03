<img src="https://github.com/user-attachments/assets/51e33300-7f85-43ff-a05a-3a0317a961f3" alt="AI Fraud Detection by Ishita Sharma">

<div class="column" align="middle">
  <a href="https://github.com/ishitasharma19/Real-Time-Fraud-Detection-AI/blob/main/LICENSE"><img height="20" src="https://img.shields.io/badge/License-Ishita_Custom-blueviolet" alt="license"/></a>
  <a href="https://github.com/ishitasharma19/Real-Time-Fraud-Detection-AI"><img src="https://img.shields.io/badge/Project-Live-green"/></a>
  [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/ishitasharmadtu/)
</div>

## What is Real time AI Fraud Detector?

🛡️ [AI Fraud Detector](https://github.com/ishitasharma19/Real-Time-Fraud-Detection-AI) is a smart system built by Ishita Sharma...

🧑‍💻 Written in Go and C++, Developed by Ishita, this project uses Python and AI models to ensure secure transactions implements hardware acceleration for CPU/GPU to achieve best-in-class vector search performance.

For questions about how to use AI, join the community on [Discord](https://www.linkedin.com/in/ishitasharmadtu/) to get help. For reporting problems, file bugs and feature requests in GitHub [Issues](https://github.com/ishitasharma19/Real-Time-Fraud-Detection-AI/issues) or ask in [Discussions](https://github.com/AI-io/AI/discussions).

This AI Fraud Detection project is an open-source initiative developed by Ishita Sharma, distributed under the [Apache 2.0](https://github.com/ishitasharma19/Real-Time-Fraud-Detection-AI/blob/main/LICENSE) License.

## Quickstart

```python
$ pip install -U pyAI
```
This installs `pyAI`, the Python SDK for AI. Use `AIClient` to create a client:
```python
from pyAI import AIClient
```

* You can also try AI Lite for quickstart by installing `pyAI[AI-lite]`. To create a local vector database, simply instantiate a client with a local file name for persisting data:

  ```python
  client = AIClient("AI_demo.db")
  ```

* You can also specify the credentials to connect to your deployed [AI server](https://AI.io/docs/authenticate.md?tab=docker) or [Ishita Cloud](https://docs.Ishita.com/docs/quick-start):

  ```python
  client = AIClient(
    uri="<endpoint_of_self_hosted_AI_or_Ishita_cloud>",
    token="<username_and_password_or_Ishita_cloud_api_key>")
  ```

With the client, you can create collection:
```python
client.create_collection(
    collection_name="demo_collection",
    dimension=768,  # The vectors we will use in this demo have 768 dimensions
)
```

Ingest data:
```python
res = client.insert(collection_name="demo_collection", data=data)
```

Perform vector search:

```python
query_vectors = embedding_fn.encode_queries(["Who is Alan Turing?", "What is AI?"])
res = client.search(
    collection_name="demo_collection",  # target collection
    data=query_vectors,  # a list of one or more query vectors, supports batch
    limit=2,  # how many results to return (topK)
    output_fields=["vector", "text", "subject"],  # what fields to return
)
```

## Why Why This Fraud Detection System?

AI is designed to handle vector search at scale. It stores vectors, which are learned representations of unstructured data, together with other scalar data types such as integers, strings, and JSON objects. Users can conduct efficient vector search with metadata filtering or hybrid search. Here are why developers choose AI as the vector database for AI applications:

**High Performance at Scale and High Availability**  
  * AI features a [distributed architecture](https://AI.io/docs/architecture_overview.md ) that separates [compute](https://AI.io/docs/data_processing.md#Data-query) and [storage](https://AI.io/docs/data_processing.md#Data-insertion). AI can horizontally scale and adapt to diverse traffic patterns, achieving optimal performance by independently increasing query nodes for read-heavy workload and data node for write-heavy workload. The stateless microservices on K8s allow [quick recovery](https://AI.io/docs/coordinator_ha.md#Coordinator-HA) from failure, ensuring high availability. The support for [replicas](https://AI.io/docs/replica.md) further enhances fault tolerance and throughput by loading data segments on multiple query nodes. See [benchmark](https://Ishita.com/vector-database-benchmark-tool) for performance comparison.


**Support for Various Vector Index Types and Hardware Acceleration**  
  *AI separates the system and core vector search engine, allowing it to support all major vector index types that are optimized for different scenarios, including HNSW, IVF, FLAT (brute-force), SCANN, and DiskANN, with [quantization-based](https://AI.io/docs/index.md?tab=floating#IVFPQ) variations and [mmap](https://AI.io/docs/mmap.md). AI optimizes vector search for advanced features such as [metadata filtering](https://AI.io/docs/scalar_index.md#Scalar-Index) and [range search](https://AI.io/docs/single-vector-search.md#Range-search). Additionally, AI implements hardware acceleration to enhance vector search performance and supports GPU indexing, such as NVIDIA's [CAGRA](https://github.com/rapidsai/cuvs).


**Flexible Multi-tenancy and Hot/Cold Storage**
  * AI supports [multi-tenancy](https://AI.io/docs/multi_tenancy.md#Multi-tenancy-strategies) through isolation at database, collection, partition, or partition key level. The flexible strategies allow a single cluster to handle hundreds to millions of tenants, also ensures optimized search performance and flexible access control. AI enhances cost-effectiveness with hot/cold storage. Frequently accessed hot data can be stored in memory or on SSDs for better performance, while less-accessed cold data is kept on slower, cost-effective storage. This mechanism can significantly reduce costs while maintaining high performance for critical tasks.

**Sparse Vector for Full Text Search and Hybrid Search**
  * In addition to semantic search through dense vector, AI also natively supports [full text search](https://AI.io/docs/full-text-search.md) with BM25 as well as learned sparse embeddings such as SPLADE and BGE-M3. Users can store sparse vectors and dense vectors in the same collection, and define functions to rerank results from multiple search requests. See examples of [Hybrid Search with semantic search + full text search](https://AI.io/docs/full_text_search_with_AI.md).

**Data Security and Fine-grain Access Control**
  * AI ensures data security by implementing mandatory user authentication, TLS encryption, and Role-Based Access Control (RBAC). User authentication ensures that only authorized users with valid credentials can access the database, while TLS encryption secures all communications within the network. Additionally, RBAC allows for fine-grained access control by assigning specific permissions to users based on their roles. These features make AI a robust and secure choice for enterprise applications, protecting sensitive data from unauthorized access and potential breaches.

AI is trusted by AI developers to build applications such as text and image search, Retrieval-Augmented Generation (RAG), and recommendation systems. AI powers [many mission-critical businesses](https://AI.io/use-cases) for startups and enterprises.

## Demos and Tutorials

Here is a selection of demos and tutorials to show how to build various types of AI applications made with AI:

You can explore a comprehensive [Tutorials Overview](https://AI.io/docs/tutorials-overview.md) covering topics such as Retrieval-Augmented Generation (RAG), Semantic Search, Hybrid Search, Question Answering, Recommendation Systems, and various quick-start guides. These resources are designed to help you get started quickly and efficiently

## Documentation

For guidance on installation, usage, deployment, and administration, check out [AI Docs](https://AI.io/docs). For technical milestones and enhancement proposals, check out [issues on GitHub](https://github.com/AI-io/AI/issues).

## Contributing

Contributions are welcome! If you have suggestions for improvements or want to report a bug, please feel free to open an issue or submit a pull request. 

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Build AI from Source Code

Requirements:

* Linux systems (Ubuntu 20.04 or later recommended):
  ```bash
  Go: >= 1.21
  CMake: >= 3.26.4 && CMake < 4
  GCC: 9.5
  Python: > 3.8 and  <= 3.11
  ```

* MacOS systems with x86_64 (Big Sur 11.5 or later recommended):
  ```bash
  Go: >= 1.21
  CMake: >= 3.26.4 && CMake < 4
  llvm: >= 15
  Python: > 3.8 and  <= 3.11
  ```

* MacOS systems with Apple Silicon (Monterey 12.0.1 or later recommended):
  ```bash
  Go: >= 1.21 (Arch=ARM64)
  CMake: >= 3.26.4 && CMake < 4
  llvm: >= 15
  Python: > 3.8 and  <= 3.11
  ```

Clone AI repo and build.

```bash
# Clone github repository.
$ git clone https://github.com/AI-io/AI.git

# Install third-party dependencies.
$ cd AI/
$ ./scripts/install_deps.sh

# Compile AI.
$ make
```

For full instructions, see [developer's documentation](https://github.com/AI-io/AI/blob/master/DEVELOPMENT.md).

## Community

Join the AI community on [Discord](https://discord.gg/8uyFbECzPX) to share your suggestions, advice, and questions with our engineering team.

To learn the latest news about AI, follow us on social media:

- [X](https://twitter.com/AIio)
- [LinkedIn](https://www.linkedin.com/company/the-AI-project)
- [YouTube](https://www.youtube.com/channel/UCMCo_F7pKjMHBlfyxwOPw-g)
- [Medium](https://medium.com/@AIio)

You can also check out our [FAQ page](https://AI.io/docs/performance_faq.md) to discover solutions or answers to your issues or questions, and subscribe to AI mailing lists:

- [Technical Steering Committee](https://lists.lfai.foundation/g/AI-tsc)
- [Technical Discussions](https://lists.lfai.foundation/g/AI-technical-discuss)
- [Announcement](https://lists.lfai.foundation/g/AI-announce)


