---
language:
- en
license: apache-2.0
size_categories:
- 1K<n<10K
task_categories:
- text-classification
tags:
- speciesism
- bias
- animal-rights
- ethics
- nlp
- fairness
pretty_name: Speciesism Bias Dataset
dataset_info:
  features:
  - name: id
    dtype: string
  - name: text
    dtype: string
  - name: speciesist_label
    dtype: string
  - name: category
    dtype: string
  - name: species_context
    dtype: string
  - name: paired_id
    dtype: string
  - name: source_type
    dtype: string
  splits:
  - name: train
    num_examples: 1506
---

# Speciesism Bias Dataset

Paired examples for evaluating speciesist bias in language models and NLP systems.

Each pair presents the same semantic content framed in two ways:
- **Speciesist**: using industry-standard language that objectifies, euphemizes, or deindividuates animals
- **Non-speciesist**: using accurate, rights-based, or agency-recognizing language

## Dataset Structure

| Column | Description |
|--------|-------------|
| `id` | Unique identifier (s=speciesist, n=non-speciesist, t=neutral) |
| `text` | The example sentence |
| `speciesist_label` | "speciesist", "non_speciesist", or "neutral" |
| `category` | Framing category (objectification, euphemism, deindividuation, industry_normalization, property_framing, rights_language, agency_language, accurate_language, neutral) |
| `species_context` | Species referenced (cattle, chickens, pigs, fish, sheep, goats, ducks, turkeys, geese, horses, dogs, cats, rabbits, wildlife, mixed) |
| `paired_id` | ID of the paired counterpart |
| `source_type` | "synthetic" (template-generated) |

## Categories

### Speciesist Framing
- **Objectification**: Treating sentient beings as commodities ("livestock", "production animal", "unit")
- **Euphemism**: Sanitized language about killing ("harvested", "processed", "depopulated")
- **Deindividuation**: Removing individual identity ("batch", "inventory", "throughput")
- **Industry normalization**: Normalizing exploitation systems ("feedlot", "gestation crate")
- **Property framing**: Framing animals as property ("chattel", "vermin", "game animal")

### Non-Speciesist Framing
- **Rights language**: Recognizing moral status ("sentient being", "animal liberation")
- **Agency language**: Attributing emotions and individuality ("grieved", "personality")
- **Accurate language**: Direct description ("killed" not "harvested", "confined" not "housed")

## Usage

```python
from datasets import load_dataset
ds = load_dataset("open-paws/speciesism-bias-dataset")

# Get paired examples
speciesist = [r for r in ds["train"] if r["speciesist_label"] == "speciesist"]
non_speciesist = [r for r in ds["train"] if r["speciesist_label"] == "non_speciesist"]
```

## Citation

```bibtex
@misc{speciesism_bias_2026,
  title={Speciesism Bias Dataset},
  author={Open Paws},
  year={2026},
  publisher={GitHub},
  url={https://github.com/Open-Paws/speciesism-bias-dataset}
}
```

## References

- Singer, P. (1975). *Animal Liberation*. New York Review/Random House.
- Dunayer, J. (2001). *Animal Equality: Language and Liberation*. Ryce Publishing.
- Stibbe, A. (2012). *Animals Erased*. Wesleyan University Press.
