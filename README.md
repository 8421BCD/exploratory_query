# 📊 Exploratory Query Evaluation Dataset

## 📋 Overview

Welcome to the Exploratory Query Evaluation Dataset, the eval data used by our work Mining Exploratory Queries for Conversational Search\[[Paper](https://dl.acm.org/doi/pdf/10.1145/3589334.3645424)\], which had been accepted by WWW 2024! This dataset was created to facilitate the evaluation of our exploratory query generation task. We sampled 100 queries randomly from the MIMICS dataset to create the evaluation data.

## 📄 Dataset Details

- **Dataset Size**: This dataset comprises 100 real user queries, randomly sampled from the MIMICS-Click dataset.
- **Query Statistics**: On average, each query contains 1.69 exploratory query groups and 15.48 exploratory queries. Each exploratory query group, on average, contains 9.16 exploratory queries.
- **Data Format**: The dataset is available in JSON format. The name of each JSON file represents a real user query.

## 🌐 Data Collection Process
For each query, we aggregate exploratory queries generated by all models (including the ablation models and baselines) we want to evaluate and the human-written ones to form a pool. Note that such aggregation follows the classic Cranfield experiments, which aims to ensure a fair evaluation of all models. We hired three annotators who have a Master’s degree with compensation to help select high-quality exploratory queries to construct the final ground truth. Specifically, we ask the annotators to evaluate these exploratory queries in terms of three aspects: usefulness, faithfulness, and readability. We give them the definition (see the Table) and some examples to help them better understand these aspects. If an exploratory query satisfies all three aspects, then a Good label should be given. Otherwise, they are asked to give a Bad label. The final label of each exploratory query is determined by the majority vote among the three annotators.

| Aspect    | Definition |
|-----------|------------|
| Usefulness | The exploratory query is parallel to the original user query and can meet users’ exploratory needs. |
| Faithfulness | The exploratory query should make sense and provides faithful information that users can trust. |
| Readability | The exploratory query is free of grammatical errors, smooth and easy to understand. |

Finally, we manually create exploratory groups for each query (such as “Cartier women [MASK]” for the query “Cartier women watches”) and assign the exploratory queries whose final labels are Good in the pool to corresponding created groups as the ground-truth.

## 📝 Data Format

Here is an example from the dataset:
adidas jeans.json
```json
[
    {
        "template": "[MASK] jeans",
        "ground_truth": [
            "calvin klein jeans",
            "tommy jeans",
            "converse jeans",
            "tommy hilfiger jeans",
            "clarks jeans",
            "nike jeans",
            "puma jeans",
            "hugo boss jeans",
            "new balance jeans",
            "reebok jeans",
            "wrangler jeans",
            "levis jeans",
            "fila jeans",
            "lee jeans"
        ]
    },
    {
        "template": "adidas [MASK]",
        "ground_truth": [
            "adidas shorts",
            "adidas pajamas",
            "adidas shoes",
            "adidas sweatpants",
            "adidas coats & jackets",
            "adidas pants",
            "adidas sweaters",
            "adidas shirts",
            "adidas track pants",
            "adidas jacket",
            "adidas hoodie",
            "adidas sweatshirts",
            "adidas sneakers"
        ]
    }
]
```
The 'adidas jeans' is the original user query. The "ground_truth" field represents an exploratory query group, which contains a list of high-quality exploratory queries used for model evaluation. The '[MASK]' in the 'template' field represents the replaced term in the original query.
## 📝 Future Work
In the future, we will expand the size of the dataset and add an exploratory question for each exploratory query group (e.g., 'What other brands are you also interested in?' for group '[MASK] jeans') to make our dataset better suited for conversational search scenarios.

