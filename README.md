# WPSOLR Stacks

![Docker](https://img.shields.io/badge/docker-ready-blue)
![WordPress](https://img.shields.io/badge/wordpress-compatible-21759b)
![License](https://img.shields.io/badge/license-Apache%202.0-blue)

This repository contains **Docker Compose examples** for running **WPSOLR** environments.
It helps developers quickly spin up WPSOLR with supporting search engines.

---

## Contents

| Stack                                                                                                                                                                                                                 | Description                                  | Folder                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------|--------------------------------------|
| ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=white) ![TimescaleDB](https://img.shields.io/badge/TimescaleDB-2EC1AC?logo=timescaledb&logoColor=white)                        | WPSOLR with PostgreSQL / TimescaleDB backend | [`postgresql/`](postgresql)          |
| ![Elasticsearch](https://img.shields.io/badge/Elasticsearch-6CC24A?logo=elasticsearch&logoColor=white)                                                                                                                | WPSOLR with Elasticsearch backend            | [`elasticsearch/`](elasticsearch)    |
| ![OpenSearch](https://img.shields.io/badge/OpenSearch-0073BB?logo=opensearch&logoColor=white)                                                                                                                         | WPSOLR with OpenSearch backend               | [`opensearch/`](opensearch)          |
| ![Apache SolrCloud](https://img.shields.io/badge/Apache%20Solr-F05A28?logo=apache-solr&logoColor=white)  [![ZooKeeper](https://img.shields.io/badge/ZooKeeper-blue?logo=apachezookeeper&logoColor=white)](Zookeeper)  | WPSOLR with Apache SolrCloud backend         | [`apache-solrcloud/`](apache-solrcloud) |
| ![Weaviate](https://img.shields.io/badge/Weaviate-00CFFF?logo=weaviate&logoColor=white)                                                                                                                               | WPSOLR with Weaviate backend                 | [`weaviate/`](weaviate)              |
| ![Vespa.ai](https://img.shields.io/badge/Vespa.ai-FF2D20?logo=vespa&logoColor=white)                                                                                                                                  | WPSOLR with Vespa.ai backend                 | [`vespa-ai/`](vespa-ai)     |
| ![Qdrant](https://img.shields.io/badge/Qdrant-0093DD?logo=qdrant&logoColor=white)                                                                                                                                     | WPSOLR with Qdrant backend                   | [`qdrant/`](qdrant) (soon)           |

Each folder contains a `docker-compose.yml` and instructions to run the stack.

