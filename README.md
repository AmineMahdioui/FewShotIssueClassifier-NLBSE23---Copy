---
pipeline_tag: sentence-similarity
tags:
- sentence-transformers
- Text Classification
license: gpl-3.0
language:
- en
---

# FewShotIssueClassifier-NLBSE23

This is a SetFit model using Sentence Transformers to map sentences & paragraphs to a 768 dimensional dense vector space. It be used for tasks like clustering or semantic search.

<!--- Describe your model here -->
This specific model is fine-tuned for Issue Report Classification in 4 classes: bug, documentation, feature, question

## Usage

You can use the model like this:

```python
from sentence_transformers.losses import CosineSimilarityLoss
from setfit import SetFitModel
from setfit import SetFitTrainer
sentences = ["error in line 20", "add method list_features"]

label_mapping = {
  0 : "bug",
  1 : "documentation",
  2 : "feature",
  3 : "question"
}

model = SetFitModel.from_pretrained('PeppoCola/FewShotIssueClassifier-NLBSE23')
predictions = model.predict(sentences)
print([label_mapping[i] for i in predictions])
```

## Dataset
This model is trained on a subset of the [NLBSE23](https://nlbse2023.github.io/tools/) dataset. The sample was hand-labeled, and made available on [Zenodo](https://zenodo.org/record/7628150#.ZBnM3XbMJD8)

## Citing & Authors

```
@software{Colavito_Few-Shot_Learning_for_2023,
	title        = {{Few-Shot Learning for Issue Report Classification}},
	author       = {Colavito, Giuseppe and Lanubile, Filippo and Novielli, Nicole},
	year         = 2023,
	month        = 2,
	url          = {https://github.com/collab-uniba/Issue-Report-Classification-NLBSE2023},
	version      = {1.0.0}
}

```

```
@dataset{colavito_giuseppe_2023_7628150,
  author       = {Colavito Giuseppe and
                  Lanubile Filippo and
                  Novielli Nicole},
  title        = {Few-Shot Learning for Issue Report Classification},
  month        = feb,
  year         = 2023,
  note         = {{To use this, merge the CSV with the original 
                   dataset (after removing duplicates on the 'id'
                   column)}},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.7628150},
  url          = {https://doi.org/10.5281/zenodo.7628150}
}
```

```
@inproceedings{Colavito-2023,
	title        = {Few-Shot Learning for Issue Report Classification},
	author       = {Colavito, Giuseppe and Lanubile, Filippo and Novielli, Nicole},
	year         = 2023,
	booktitle    = {2nd International Workshop on Natural Language-Based Software Engineering (NLBSE)}
}
```