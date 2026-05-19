# Language Models are Few-Shot Learners
**Authors:**  Brown et al.2020

---

## Summary

Fine-tuning requires labeled data,time and resources for every new task. GPT 3 tries to solve this limitation by allowing us to use the same base model but with examples.
Eg : 
- Zero Shot: "Give me a pizza recipe." In Zero Shot we just tell the model a specific task.

- One Shot: "Give me exact stepwise pizza recipe by referring to the burger recipe." Here we show one example to the model which allows the model to generate similar output to our example.

- Few Shot: "Give me exact stepwise pizza recipe by reffering to the recipe book." We share multiple examples so that the model recognises the pattern we want it to follow.


## Key Concepts

### 1. Architecture

The GPT-3 is not architecturally novel but the alterating dense and sparse layers is what makes it distinct from the GPT-2 along with 100x bump in training parameters 1.5B -> 175B. The shallow models are uncapable of few shot prompting, it emerges wit scale.

### 2. Training Data

Data is the big contributor to GPT 3. Starting with Common Crawl (basically scrape the entire internet) ~ 570GB of text after filtering. The aggressive filtering ensures the removal of noise, keeping only documents similar to high-quality sources like Reddit upvote links.

*The quality filtering and upweighting high-quality sources mattered as much as the raw scale*

### 3. Limitations

- Repetition and coherence degrade on long text generation
- Bidirectional context — GPT-3 only sees left context (it's a decoder). BERT sees both directions, which is better for understanding tasks. GPT-3 is better for generation.
- Sample inefficiency — it trained on 300B tokens. Humans learn language from far less. Something is missing in how it learns.
- Interpretability — nobody really knows what's happening inside the weights when it does few-shot learning. Is it actually "learning" in-context or just sophisticated pattern matching? Still an open question.
- Bias and toxicity — trained on internet data, reflects internet biases. They tested this and documented it.


### 4. GPT-3 vs BERT

- **GPT** is decoder only. It can only refer to the text on the left. Performs exceptionally well for text generation (predicting the next token)

- **BERT** is bi-directional encoder. It can refer to both left and right. This helps BERT to understand the value of the current token. Typically used to understand the whole context of the corpus.


| | GPT-3 | BERT |
|---|---|---|
| Architecture | Decoder | Encoder |
| Context | Left only | Bidirectional |
| Strength | Generation | Understanding |
| Adaptation | Few-shot in prompt | Fine-tuning |