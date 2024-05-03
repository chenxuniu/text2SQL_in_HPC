# text2SQL in HPC

## Introduction and Motivation

Scientific applications，experiments and observations often store massive amounts of data in various scientific file formats. Natural language interfaces allow users to interact with
complex data systems in a manner that’s akin to human conversation. This reduces the cognitive load and learning curve, as users don’t need to learn specialized query syntax or understand the underlying data architecture. In order to provide natural language processing, most existing methods will use text2SQL methods. 


We investigate various text2SQL approaches, including rule-based, template-based, and machine learning models, particularly focusing on their adaptability and performance in HPC settings characterized by large-scale data processing requirements. The findings reveal significant disparities among the methods in terms of efficiency and scalability, highlighting the challenges and potential of integrating text2SQL systems in HPC environments. This study not only benchmarks the current state of Text2SQL technologies in demanding contexts but also lays the groundwork for future advancements in bridging natural language processing and high-performance database systems.

## The Problem to Compute


1. Which of the implementations are viable in an HPC setting?  
2. How do these methods compare in terms of training time, query time, memory usage, cost effectiveness, accuracy, and scalability? \label{item:2}
3. How can training datasets for text2SQL systems be effectively parallelized in an HPC environment, and what are the key strategies for managing data distribution and load balancing? (Split the dataset into smaller chunks that can be distributed across multiple computing nodes. The partitioning should aim to minimize dependencies between data chunks to enhance parallel processing.)
4. What methods are best to parallelize tasks in text2SQL processing, and how do they contribute to handling larger query volumes and reducing response times?
5. What challenges arise with parallel processing in text2SQL systems, particularly concerning synchronization, communication overhead, and data consistency?

## Models to evaluate

- (2023-AAAI 2023, CCF-A) **RESDSQL**: Decoupling Schema Linking and Skeleton Parsing for Text-to-SQL
[[paper](https://arxiv.org/pdf/2302.05965.pdf)]
[[code](https://github.com/RUCKBReasoning/RESDSQL)]
[![](https://img.shields.io/badge/Spider-green)](https://yale-lily.github.io/spider)
[![](https://img.shields.io/badge/Spider--Realistic-yellow)](https://aclanthology.org/2021.naacl-main.105.pdf)
[![](https://img.shields.io/badge/Spider--DK-blue)](https://arxiv.org/pdf/2109.05157.pdf)
[![](https://img.shields.io/badge/Spider--Syn-red)](https://arxiv.org/pdf/2106.01065.pdf)

- (2022-ACL, CCF-A) **S<sup>2</sup>SQL**: Injecting Syntax to Question-Schema Interaction Graph Encoder for Text-to-SQL Parsers
[[paper](https://aclanthology.org/2022.findings-acl.99.pdf)]
[![](https://img.shields.io/badge/Spider-green)](https://yale-lily.github.io/spider)
[![](https://img.shields.io/badge/Spider--Syn-yellow)](https://arxiv.org/pdf/2106.01065.pdf)

- (2021-EMNLP, CCF-B) **PICARD**:Parsing Incrementally for Constrained Auto-Regressive Decoding from Language Models
[[paper](https://arxiv.org/pdf/2109.05093v1.pdf)]
[[code](https://github.com/ServiceNow/picard)]
[![](https://img.shields.io/badge/Spider-green)](https://yale-lily.github.io/spider)
[![](https://img.shields.io/badge/CoSQL-yellow)](https://arxiv.org/pdf/1909.05378.pdf)

- (2022-EMNLP, CCF-B) **RASAT**: Integrating Relational Structures into Pretrained Seq2Seq Model
for Text-to-SQL
[[paper](https://arxiv.org/pdf/2205.06983v2.pdf)]
[[code](https://github.com/LUMIA-group/rasat)]
[![](https://img.shields.io/badge/Spider-green)](https://yale-lily.github.io/spider)
[![](https://img.shields.io/badge/SParC-yellow)](https://arxiv.org/pdf/1906.02285.pdf)
[![](https://img.shields.io/badge/CoSQL-blue)](https://arxiv.org/pdf/1909.05378.pdf)

- (2023-arXiv, None) **MAC-SQL**: A Multi-Agent Collaborative Framework for Text-to-SQL
[[paper](https://arxiv.org/pdf/2312.11242.pdf)]
[[code](https://github.com/wbbeyourself/MAC-SQL)]
[![](https://img.shields.io/badge/Spider-green)](https://yale-lily.github.io/spider)
[![](https://img.shields.io/badge/BIRD-yellow)](https://bird-bench.github.io/)

- (2020-EMNLP, CCF-B) Bridging Textual and Tabular Data for Cross-Domain Text-to-SQL Semantic Parsing
[[paper](https://arxiv.org/pdf/2012.12627v2.pdf)]
[[code](https://github.com/salesforce/TabularSemanticParsing)]
[![](https://img.shields.io/badge/Spider-green)](https://yale-lily.github.io/spider)
[![](https://img.shields.io/badge/WikiSQL-yellow)](https://github.com/salesforce/WikiSQL/blob/master/README.md)

- (2020-ACL, CCF-A) **RAT-SQL**: Relation-Aware Schema Encoding and Linking for Text-to-SQL Parsers
[[paper](https://arxiv.org/pdf/1911.04942v5.pdf)]
[[code](https://github.com/Microsoft/rat-sql)]
[![](https://img.shields.io/badge/Spider-green)](https://yale-lily.github.io/spider)
[![](https://img.shields.io/badge/WikiSQL-yellow)](https://github.com/salesforce/WikiSQL/blob/master/README.md)

- (2018-EMNLP, CCF-B) **SyntaxSQLNet**: Syntax Tree Networks for Complex and Cross-DomainText-to-SQL Task
[[paper](https://arxiv.org/pdf/1810.05237v2.pdf)]
[[code](https://github.com/taoyds/syntaxsql)]
[![](https://img.shields.io/badge/Spider-green)](https://yale-lily.github.io/spider)

- (2018-NAACL, CCF-B) **TypeSQL**: Knowledge-based Type-Aware Neural Text-to-SQL Generation
[[paper](https://arxiv.org/pdf/1804.09769.pdf)]
[[code](https://github.com/taoyds/typesql)]
[![](https://img.shields.io/badge/WikiSQL-green)](https://github.com/salesforce/WikiSQL/blob/master/README.md)

- (2017-arXiv, None) **SQLNet**: Generating Structured Queries From Natural Language Without Reinforcement Learning
[[paper](https://arxiv.org/pdf/1711.04436.pdf)]
[[code](https://github.com/xiaojunxu/SQLNet)]
[![](https://img.shields.io/badge/WikiSQL-green)](https://github.com/salesforce/WikiSQL/blob/master/README.md)
