# Replicating Lee (2008), "Randomized Experiments from Non-random Selection in U.S. House Elections"

## The paper and its headline claim

Paper: Lee, David S. (2008). "Randomized Experiments from Non-random Selection in U.S. House Elections." Journal of Econometrics, 142(2), 675–697.

Identification strategy: Regression discontinuity design (RDD).

Headline claim: Lee (2008) finds that narrowly winning an election increases a party's vote share in the next election. The paper estimate used in my comparison is 0.077.

My replication: My estimate is 0.0815, compared with the paper estimate of 0.077. The difference is 5.83%. My estimate is slightly higher, possibly because of differences in sample selection and model specification.


## Reproduce the headline table

Python 3.11 or newer. From the repository root:

```bash
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python reproduce.py
```

`python reproduce.py` is the one command. Once `MY_PAPER` is set in `download_data.py`,
it downloads the data if `data/` does not have it, runs `notebooks/01_positioning_and_replication.ipynb` and then
`notebooks/02_robustness.ipynb` top to bottom in a fresh kernel, and prints the headline
table from `output/headline_table.csv`. Executed copies of the notebooks, with their
outputs, go to `output/executed/`.

- **Expected runtime:** About 10 seconds for both notebooks in my current environment, excluding package installation.

## Data: source and licence
 **Source:** I use the U.S. House election data from Lee (2008), downloaded from the Causal Inference: The Mixtape GitHub repository.

- **Included or downloaded:** The data are downloaded using `download_data.py` rather than included in the repository.

## Repository map

| Path | What it is |
|---|---|
| `reproduce.py` | The one command: runs the notebooks in name order, prints the headline table |
| `download_data.py` | Data URLs for the six papers; `python download_data.py --paper card` fetches one into `data/` |
| `notebooks/01_positioning_and_replication.ipynb` | Sections 1 and 2: positioning notes, the replication, the theirs-vs-mine table, the discrepancy log. **No AI.** |
| `notebooks/02_robustness.ipynb` | Section 3: four robustness exercises. AI allowed, logged in `ai-appendix.md` |
| `output/headline_table.csv` | The theirs-vs-mine table, written by notebook 01 |
| `output/density_test.csv` | Results from the density test near the election cutoff |
| `output/vote_margin_histogram.png` | Histogram of vote margins around the 50% cutoff |
| `output/` | Every table and figure the report uses |
| `report/` | The report PDF |
| `ai-appendix.md` | P.R.I.M.E. entries and full transcripts for Sections 3 to 6, and the no-AI statement for Sections 1 and 2 |
| `AUDIT.md` | How to run the peer audit you file on a classmate's repository |
| `requirements.txt` | Pinned package versions |

## Use of AI

Sections 1 and 2 were completed without AI.

TODO: list the sections where you used AI (from 3, 4, 5 and 6), for what, and point to the
entries in [`ai-appendix.md`](ai-appendix.md). If you used none, say so.