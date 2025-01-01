# RAG Eval Tool

`rag_eval_tool` is a comprehensive evaluation library for analyzing the performance of text generation systems. It provides a variety of metrics to assess the quality, diversity, readability, bias, and overall accuracy of generated text in comparison to reference texts.

---

## Installation

Install the library directly from PyPI:

```bash
pip install rag_eval_tool
```

---

## Features

`RAG Eval Tool` offers evaluation capabilities for:

### 1. **BLEU and ROUGE Scores**
   - `BLEU`: Measures n-gram overlap between candidate and reference texts.
   - `ROUGE`: Measures recall-oriented overlap, including ROUGE-1, ROUGE-2, and ROUGE-L.

### 2. **BERTScore**
   - Leverages BERT embeddings to compute Precision, Recall, and F1 scores.

### 3. **Perplexity**
   - Evaluates fluency by computing the perplexity of the generated text using GPT-2.

### 4. **Diversity**
   - Measures the ratio of unique bigrams in the text to assess lexical diversity.

### 5. **Racial Bias Detection**
   - Uses a zero-shot classification model to evaluate potential bias in the text.

### 6. **METEOR and CHRF**
   - `METEOR`: Measures alignment of unigrams with stemming, synonymy, and order weighting.
   - `CHRF`: Measures character n-gram F-score.

### 7. **Readability**
   - Calculates:
     - Flesch Reading Ease Score
     - Flesch-Kincaid Grade Level

### 8. **Hallucination**
   - Detects tokens in the generated text that do not appear in the reference text.

### 9. **Precision, Recall, and F1**
   - Token-level comparison between generated and reference text.

### 10. **Entropy**
   - Measures the entropy of tokens in the text for lexical diversity.

---

## Usage

### Importing the Library

```python
from rag_eval_tool import RAG_Eval_Tool
```

### Initialization

```python
# Initialize the evaluation tool
rag_eval = RAG_Eval_Tool()
```

### Evaluate All Metrics

The `evaluate_all` function provides a comprehensive evaluation of a generated response against a reference text using all supported metrics. This function returns a dictionary containing the following metrics:

- **BLEU**: N-gram overlap score.
- **ROUGE-1**: Recall-oriented overlap of unigrams.
- **BERT P, R, F1**: Precision, Recall, and F1 scores based on BERT embeddings.
- **Perplexity**: Measures fluency using GPT-2.
- **Diversity**: Ratio of unique bigrams to total tokens.
- **Racial Bias**: Probability that the text contains biased or hateful content.
- **METEOR**: Alignment of unigrams with semantic similarity.
- **CHRF**: Character-level F-score.
- **Flesch Reading Ease**: Readability score for the text.
- **Flesch-Kincaid Grade**: Grade level readability score.
- **Hallucination**: Tokens present in the response but not in the reference.
- **Precision, Recall, and F1**: Token-level comparison metrics.
- **Entropy**: Lexical diversity measure.

#### Example Usage
```python
response = "The generated text to be evaluated."
reference = "The reference text for comparison."

results = rag_eval.evaluate_all(response, reference)

# Print evaluation results
for metric, value in results.items():
    print(f"{metric}: {value}")
```

This function is designed for easy integration into text evaluation pipelines, allowing for detailed insights into multiple facets of text quality, diversity, and fairness.

### Evaluate Individual Metrics

#### BLEU and ROUGE
```python
bleu, rouge1 = rag_eval.evaluate_bleu_rouge([response], [reference])
print("BLEU:", bleu)
print("ROUGE-1:", rouge1)
```

#### Perplexity
```python
ppl = rag_eval.evaluate_perplexity(response)
print("Perplexity:", ppl)
```

#### Diversity
```python
diversity = rag_eval.evaluate_diversity([response])
print("Diversity:", diversity)
```

#### Readability
```python
flesch_ease, flesch_grade = rag_eval.evaluate_readability(response)
print("Flesch Reading Ease:", flesch_ease)
print("Flesch-Kincaid Grade:", flesch_grade)
```

---

## Dependencies

`rag_eval_tool` requires the following dependencies:

- `torch`
- `transformers`
- `sacrebleu`
- `rouge-score`
- `bert-score`
- `nltk`
- `textstat`
- `scikit-learn`
- `numpy`

All required dependencies are installed automatically with the library.

---

## License

This library is open-source and available under the MIT License. Feel free to use, modify, and distribute it as needed.

---

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to open a pull request or issue on the GitHub repository.

---

## Acknowledgments

- **Hugging Face Transformers** for models like GPT-2 and DeHateBERT.
- **NLTK** for natural language processing utilities.
- **SacreBLEU, ROUGE-Score, and BERTScore** for evaluation metrics.

---

## Example Project

For a complete example of how to use `rag_eval_tool` in a text generation evaluation pipeline, please check the example notebook in the repository.

---

## Contact

For questions or feedback, please reach out to [Your Name or Email].

