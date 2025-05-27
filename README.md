# SQuAD-v2 Answer-Span Extraction (BERT-base)

This repo shows how far a single, straightforward BERT-base can go on the formidable SQuAD 2.0 dataset, even when we only let it look at 30 % of the data. Turns out: 0.82 F1 on the dev set. Definitely not too shabby for a three-epoch sprint.

## Dataset  

Stanford Question Answering Dataset 2.0 – passages + questions; some questions have no answer, but in this project we train BERT only to extract spans for answerable items.  

## Contents  

`data/`
- `dataset.md` - Source and description for the Amazon Fine-Food dataset.

`notebooks/`   
- `notebook.md` - Link to the Colab notebook that runs every experiment.

## Results   

| Model / Setting                         | Train Split   | Metric | Score         |
| --------------------------------------- | ------------- | ------ | ------------- |
| **BERT-base QA** (3 epochs, lr = 5 e-5) | 30 % of SQuAD | F1     | **0.62**      |


## Takeaways  

- Even a fraction (30 %) of SQuAD is enough for BERT to learn solid span-finding skills.
- Clean convergence was ensured with training & validation loss drop in lock-step (see notebook charts).
- Biggest misses stem from answers clipped by the 512-token limit a sliding-window stride should close the gap.  Might re-visit later to optimize this.

