# Smell Prediction

The training and test data are in the [data](data/) folder. This data is the English part from the [Odeuropa Benchmark](https://github.com/Odeuropa/benchmarks_and_corpora). The XML files were converted to BIO using the [format_converter.py](https://github.com/Odeuropa/benchmarks_and_corpora/tree/converters) converter script. Next, any sentence that contain a token-level annotation is marked as positive. The sentences are shuffled and split as training (2,491) and test files (650 documents).

The code utilized to create the models is on 

We pick the best model out of [BERT](https://huggingface.co/bert-base-uncased), [RoBERTa](https://huggingface.co/roberta-base), and [macBERTH](https://github.com/emanjavacas/macberth-eval) after created five models for each one using different random seeds. macBERTh yield the best results in average. The code for training and testing the models is on this [repo](https://github.com/Odeuropa/transformers_text_classification/). The commit for reproducing this work is [fa7f8a27a3822c33ecfd854a5206c10c83ef4a37](https://github.com/Odeuropa/transformers_text_classification/tree/fa7f8a27a3822c33ecfd854a5206c10c83ef4a37). Use the following commands to see the version used for this work: 
1. git clone -n <repo_name> 
2. one of the following commands: 
    - git checkout -b <new_branch> <commit_sha> 
    - git checkout <commit_sha> 

Utilizing this best model, we have predicted the sentences of the fairy tales. The predictions are in the [results](results/) folder:
- [predictions_bert_emotions_csv_macBERTh-uncased_64_64_0.10_46.jsonl](results/predictions_bert_emotions_csv_macBERTh-uncased_64_64_0.10_46.jsonl): all sentences with their predictions
- [predictions_bert_emotions_csv_macBERTh-uncased_64_64_0.10_46.jsonl](results/predictions_bert_emotions_csv_macBERTh-uncased_64_64_0.10_46-POSITIVES.jsonl): sentences that are predicted as containing smell
- [predictions_bert_emotions_csv_macBERTh-uncased_64_64_0.10_46.jsonl](results/predictions_bert_emotions_csv_macBERTh-uncased_64_64_0.10_46-NEGATVES.jsonl): sentences that are predicted as NOT containing smell