
# DictaLM-2.0-Instruct Fine-Tuning Project

This project aims to enhance the performance of the DictaLM-2.0-Instruct model by fine-tuning it on a bilingual (English-Hebrew) dataset. The project utilizes a unique dataset derived from the alpaca-gpt4 English data, which has been translated into Hebrew to create a rich, bilingual resource for training.

## Project Overview

The DictaLM-2.0-Instruct, a model provided by Hugging Face and tailored for instruction-based tasks, is fine-tuned here to improve its responsiveness and accuracy in two specific tasks:
1. **Question-Answering in Hebrew:** Direct question to answer mappings in Hebrew.
2. **Bilingual Translation Tasks:** Translation of questions and answers between English and Hebrew.

To prevent catastrophic forgetting, particularly in the model's ability to handle English, 10% of the training data is retained in English.

### Fine-Tuning Methodology

The model is fine-tuned using the LoRA (Low-Rank Adaptation) technique, which allows for efficient adaptation of large language models with minimal updates to the model's parameters. This method is particularly suited for adapting a model to new languages and tasks without extensive retraining.

## Dataset

The dataset, derived from the alpaca-gpt4 database, includes:
- Translations of the original English content into Hebrew.
- Retention of 10% original English questions to maintain language versatility.
- The dataset is split into training, validation, and test sets to ensure thorough evaluation.

## Usage

To use this model for either of the fine-tuned tasks, follow these steps:

### Setup

Ensure you have Python and the necessary libraries installed:

```bash
pip install transformers torch
```

### Running the Model

Import the model and tokenizer:

```python
from transformers import AutoModelForCausalLM, AutoTokenizer

model = AutoModelForCausalLM.from_pretrained("your-model-path")
tokenizer = AutoTokenizer.from_pretrained("your-model-path")
```

Example code to use the model:

```python
def get_answer(question):
    inputs = tokenizer(question, return_tensors="pt")
    outputs = model.generate(inputs["input_ids"])
    answer = tokenizer.decode(outputs[0], skip_special_tokens=True)
    return answer

# Example usage
print(get_answer("שאלה בעברית"))
```

## Contributing

Contributions to this project are welcome! Please fork the repository, make your changes, and submit a pull request.

## Citation

If you use this model or the fine-tuned dataset, please cite:

```
[Will add citation details based on your publications or data source]
```

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

This project utilizes resources and tools from Hugging Face and is based on data from the alpaca-gpt4 project.

---
For more details on the model architecture and the fine-tuning process, visit our [project wiki](wiki-link).
