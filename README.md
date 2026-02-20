# Haystack

Haystack is an open source NLP framework that lets you use powerful Transformer-based models (like BERT, RoBERTa, or GPT-3) and LLMs (like GPT-4, Llama, or Falcon) to build applications with your text data.

## 🚀 Quick Start

```bash
pip install haystack-ai
```

```python
from haystack import Pipeline
from haystack.components.generators import OpenAIGenerator

pipe = Pipeline()
pipe.add_component("generator", OpenAIGenerator(model="gpt-3.5-turbo"))

result = pipe.run({"generator": {"prompt": "What's the capital of Germany?"}})
print(result["generator"]["replies"][0])
```

## 📚 Documentation

- [Official Documentation](https://haystack.deepset.ai/)
- [Tutorials](https://haystack.deepset.ai/tutorials)
- [API Reference](https://docs.haystack.deepset.ai/)

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](https://github.com/deepset-ai/haystack/blob/main/CONTRIBUTING.md) for details.

## 📄 License

Apache-2.0 License - see [LICENSE](LICENSE) for details.

1. related project [langchain](https://github.com/langchain-ai/langchain)
2. related project [llama_index](https://github.com/run-llama/llama_index)