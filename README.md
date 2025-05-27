# SQuAD-v2 Answer-Span Extraction (BERT-base)

This repo shows how far a single, straightforward BERT-base can go on the formidable SQuAD 2.0 dataset, even when we only let it look at 30 % of the data. 

## Dataset  

Stanford Question Answering Dataset 2.0 - 100k answerable + 53k unanswerable Q-A pairs.

## Contents  

`data/`
- `dataset.md` - Source and description for the Amazon Fine-Food dataset.

`notebooks/`   
- `notebook.md` - Link to the Colab notebook that runs every experiment.


## Top Results   

| Model / Setting                         | Train Split   | Metric | Score         |
| --------------------------------------- | ------------- | ------ | ------------- |
| **BERT-base QA** (3 epochs, lr = 5 e-5) | 10 % of SQuAD | F1     | **0.62**      |
| “UnQDetect” (binary: answerable / not)  | *design only* | –      | *in progress* |

## Takeaways  

- Even with just 30% of SQuAD, plain BERT hits ~0.82 F1 – respectable for a no-frills run.
- Loss falls cleanly every epoch → no serious over-/under-fit (see plots in the notebook).
- Most misses come from long answers spilling past the 512-token window – room for sliding-window or stride tricks.
- Detecting “I don’t know” questions is essential; the UnQDetect blueprint (see report) is next on the roadmap.

