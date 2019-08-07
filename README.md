# Enhancing Joint Entity and Relation Extraction with Language Modeling and Hierarchical Attention

Implementation of the papers
[Enhancing Joint Entity and Relation Extraction with Language Modeling and Hierarchical Attention](https://arxiv.org/abs/1804.07847).

# Requirements
* Ubuntu 16.04
* Anaconda 5.0.1
* Numpy 1.14.1
* Gensim 3.4.0
* Tensorflow 1.5.0
* PrettyTable 0.7.2

## Task
Given a sequence of tokens (i.e., sentence), (i) give the entity tag of each word (e.g., NER) and (ii) the relations between the entities in the sentence. The following example indicates the accepted input format of our multi-head selection model:


```
0	Marc		B-PER		['N']					[0]		
1	Smith		I-PER 		['lives_in','works_for']		[5,11]
2 	lives		O		['N']					[2]
3	in		O		['N']					[3]
4	New		B-LOC		['N']					[4]
5	Orleans		I-LOC		['N']					[5] 
6	and		O		['N']					[6]
7	is		O		['N']					[7]
8	hired		O		['N']					[8]
9	by		O		['N']					[9]
10	the		O		['N']					[10]
11  government		B-ORG		['N']					[11]
12	.		O		['N']					[12]
```

## Configuration
The model has several parameters such as: 
* EC (entity classification) or BIO (BIO encoding scheme)
* Character embeddings
* Ner loss (softmax or CRF)

that could be specified in the configuration files (see [config](https://github.com/ChiRenjun/Joint-extraction-with-lm-and-att/configs)).

## Run the model

```
./run.sh
```

## More details
Commands executed in ```./run.sh```:

1. Train on the training set and evaluate on the dev set to obtain early stopping epoch
```python3 train_es.py```
2. Train on the concatenated (train + dev) set and evaluate on the test set until either (1) the max epochs or (2) the early stopping limit (specified by train_es.py) is exceeded
```python3 train_eval.py```
