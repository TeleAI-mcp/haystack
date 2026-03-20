[![Contributors][contributors-src]][contributors-url]
[![Version][version-src]][version-url]
[![Build Status][build-src]][build-url]
[![Documentation Status][docs-src]][docs-url]
[![Discord][discord-src]][discord-url]

[![][banner-img]][product-url]

<p align="center">
  <a href="https://haystack.deepset.ai/">
    <img src="img/haystack_logo.svg" alt="Haystack" width="30%" />
  </a>
</p>

# Haystack 🐏

**Haystack** is an open-source AI orchestration framework for building context-engineered, production-ready LLM applications.
Design modular pipelines and agent workflows with explicit control over retrieval, routing, memory, and generation.
Built for scalable agents, RAG, multimodal applications, semantic search, and conversational systems.

-   [Explore the Haystack Docs](https://docs.haystack.ai)
-   [Read Haystack Tutorials](https://haystack.deepset.ai/tutorials)
-   [Join the Haystack Discord community](https://discord.gg/haystack)

## 🚀 Quick Start

Install Haystack 2.0 in Python 3.9+:

```sh
pip install haystack-ai
```

Create your first Retrieval Augmented Generation pipeline with just a few lines of code:

```python
from haystack import Pipeline
from haystack.components.retrievers.in_memory import InMemoryBM25Retriever
from haystack.components.generators.openai import OpenAIGenerator
from haystack.components.builders.prompt_builder import PromptBuilder
from haystack import Document

prompt_template = """
Given these documents, answer the question.
Documents:
{% for doc in documents %}
    {{ doc.content }}
{% endfor %}
Question: {{ query }}
"""

documents = [
    Document(content="Paris is the capital of France."),
    Document(content="The Eiffel Tower is located in Paris."),
]

retriever = InMemoryBM25Retriever()
prompt_builder = PromptBuilder(template=prompt_template)
generator = OpenAIGenerator(model="gpt-4")

pipeline = Pipeline()
pipeline.add_component("retriever", retriever)
pipeline.add_component("prompt_builder", prompt_builder)
pipeline.add_component("llm", generator)

pipeline.connect("retriever.documents", "prompt_builder.documents")
pipeline.connect("prompt_builder.prompt", "llm.prompt")

question = "Where is the Eiffel Tower located?"
result = pipeline.run({"retriever": {"query": question}, "prompt_builder": {"query": question}})

print(result["llm"]["replies"][0])
# The Eiffel Tower is located in Paris.
```

> **Note**: You will need to set `OPENAI_API_KEY` as an environment variable to run the code above.

Explore the [Tutorials](https://haystack.deepset.ai/tutorials) to find more examples!

## 🦙 LLMWorkshop

Learn how to build production-ready LLM applications with [LLMWorkshop](https://haystack.deepset.ai/llm-workshop).
This interactive course is designed for developers who want to master RAG systems and AI agents using Haystack.

## 📙 Documentation

| Topic | Description |
| :--- | :--- |
| [📓 Tutorials](https://haystack.deepset.ai/tutorials) | Learn how to build LLM applications with Haystack by following these step-by-step guides |
| [🐍 API Reference](https://docs.haystack.ai/reference/python-api) | Detailed documentation for the Haystack Python API |
| [🏖️ Haystack UI](https://github.com/deepset-ai/haystack-webui) | Web UI for your LLM apps |
| [🤖 Hugging Face 🤖](https://huggingface.co/haystack) | Try out Haystack models on the Hugging Face Hub |
| [📖 Glossary](https://docs.haystack.ai/concepts/glossary) | General overview of core concepts |

## 🍿 Deep Dives

If you need more in-depth explanations, check out our Deep Dives:

| Topic | Description |
| :--- | :--- |
| [RAG](https://docs.haystack.ai/concepts/rag) | Retrieval Augmented Generation explained |
| [Agents](https://docs.haystack.ai/concepts/agents) | LLMs that can execute actions |
| [Preprocessors](https://docs.haystack.ai/concepts/preprocessors) | How to preprocess your data for indexing |
| [Retrievers](https://docs.haystack.ai/concepts/retrievers) | The many ways to perform retrieval |
| [Evaluations](https://docs.haystack.ai/concepts/evaluation) | How to evaluate your LLM pipelines |
| [LLM Engines](https://docs.haystack.ai/concepts/llm-engines) | Everything about the LLM interface |

## 💙 Contributing

Thanks for your interest in contributing!

There are many ways to contribute to Haystack:
report bugs, fix bugs, improve docs, add new features.
To start your contribution journey, check out the
[Contributing Guide](CONTRIBUTING.md).

[contributors-src]: https://img.shields.io/github/contributors/deepset-ai/haystack?style=flat-square&color=blueviolet
[contributors-url]: https://github.com/deepset-ai/haystack/graphs/contributors

[version-src]: https://img.shields.io/pypi/v/haystack-ai.svg?style=flat-square
[version-url]: https://pypi.org/project/haystack-ai/

[build-src]: https://github.com/deepset-ai/haystack/actions/workflows/continuous.yml/badge.svg?branch=main
[build-url]: https://github.com/deepset-ai/haystack/actions/workflows/continuous.yml

[docs-src]: https://readthedocs.org/projects/haystack/badge/?version=latest
[docs-url]: https://docs.haystack.ai

[discord-src]: https://img.shields.io/discord/813759841454308374?color=7289da&label=Discord&logo=Discord&logoColor=white&style=flat-square
[discord-url]: https://discord.gg/haystack

[product-url]: https://haystack.deepset.ai

[banner-img]: img/banner_readme.png

1. related project [langchain-ai/langchain](https://github.com/langchain-ai/langchain)
2. related project [run-llama/llama_index](https://github.com/run-llama/llama_index)