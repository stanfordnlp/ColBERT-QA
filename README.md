## ColBERT-QA: Relevance-guided Supervision for OpenQA (TACL'21)

### ColBERT-QA is a state-of-the-art system for answering open questions over a large corpus of text like Wikipedia.

ColBERT-QA extends the scalable ColBERT retriever for open-domain QA. It introduces Relevance-Guided Supervision (RGS), an iterative weak-supervision strategy that efficiently samples accurate positives and challenging negatives for training.



### Implementation

The system implementation lives as part of the parent [ColBERT](https://github.com/stanford-futuredata/ColBERT) repository. This repository will contain instructions focused on ColBERT-QA. For the general-purpose instructions, refer to the README of the parent repository.

After cloning, make sure you obtain the code for the submodule too:

```
git submodule update --init --recursive
```

We use [Anserini](https://github.com/castorini/anserini) for the BM25 implementation, which is used to initiate the first round of RGS's weak supervision. The second and third rounds rely on ColBERT-QA itself. The default corpus is Karpukhin et al.'s [21M-passage Wikipedia 2018 dump](https://dl.fbaipublicfiles.com/dpr/wikipedia_split/psgs_w100.tsv.gz). In addition to training, indexing, and retrieval, the following scripts in the parent repository are useful for the RGS process.

- utility/supervision/triples.py
- utility/evaluation/annotate_EM.py
