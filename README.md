# text2SQL in HPC

## Introduction and Motivation

Scientific applications，experiments and observations often store massive amounts of data in various scientific file formats. Natural language interfaces allow users to interact with
complex data systems in a manner that’s akin to human conversation. This reduces the cognitive load and learning curve, as users don’t need to learn specialized query syntax or understand the underlying data architecture. In order to provide natural language processing, most existing methods will use text2SQL methods. 


We investigate various text2SQL approaches, including rule-based, template-based, and machine learning models, particularly focusing on their adaptability and performance in HPC settings characterized by large-scale data processing requirements. The findings reveal significant disparities among the methods in terms of efficiency and scalability, highlighting the challenges and potential of integrating text2SQL systems in HPC environments. This study not only benchmarks the current state of Text2SQL technologies in demanding contexts but also lays the groundwork for future advancements in bridging natural language processing and high-performance database systems.

## The Problem to Compute

