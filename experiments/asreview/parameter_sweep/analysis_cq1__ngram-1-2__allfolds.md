# cq1 parameter sweep report: ngram_range=(1,2) (all folds)
## Inputs
- TS output: `experiments/asreview/outputs/asreview_ts_cv_cq1_2026-01-05T02-37-25-581Z.json`
- PY output: `experiments/asreview/outputs/asreview_py_cv_cq1_2026-01-05T02-37-40-576962.json`
- folds: 10, topK: 100
- generated_at: 2026-01-05T11:58:30

## ①② Overlap@100 summary
- overlap@100 ratio: mean 0.89 (min 0.86, max 0.93), perfect 0/10

## ③④ Agreement & proba-diff summary
- absdiff(mean over common items, then averaged over folds): 0.03013
- absdiff(max over common items, then max over folds): 0.2759

## ⑤ Threshold/ties summary
- |ts_thr - py_thr|: mean 0.04687, max 0.06062

## Per-fold metrics
| fold | overlap@100 | ratio | common | TS-only | PY-only | absdiff_mean | absdiff_max | ts_thr | py_thr | ts_tie | py_tie |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 89 | 0.89 | 89 | 11 | 11 | 0.02697 | 0.1251 | 0.722806 | 0.745392 | 1 | 2 |
| 1 | 87 | 0.87 | 87 | 13 | 13 | 0.02973 | 0.127 | 0.670706 | 0.708055 | 1 | 1 |
| 2 | 90 | 0.9 | 90 | 10 | 10 | 0.02503 | 0.121 | 0.695984 | 0.756603 | 1 | 1 |
| 3 | 90 | 0.9 | 90 | 10 | 10 | 0.03656 | 0.1509 | 0.632339 | 0.692351 | 1 | 1 |
| 4 | 90 | 0.9 | 90 | 10 | 10 | 0.02976 | 0.1457 | 0.690432 | 0.733671 | 1 | 1 |
| 5 | 90 | 0.9 | 90 | 10 | 10 | 0.02886 | 0.15 | 0.722977 | 0.774891 | 1 | 1 |
| 6 | 86 | 0.86 | 86 | 14 | 14 | 0.03536 | 0.2759 | 0.635616 | 0.693448 | 1 | 1 |
| 7 | 93 | 0.93 | 93 | 7 | 7 | 0.02622 | 0.1559 | 0.702161 | 0.746784 | 1 | 1 |
| 8 | 88 | 0.88 | 88 | 12 | 12 | 0.03273 | 0.1313 | 0.652446 | 0.69583 | 1 | 1 |
| 9 | 87 | 0.87 | 87 | 13 | 13 | 0.03006 | 0.1234 | 0.658902 | 0.706 | 1 | 1 |

## ⑥ Global Top10 probability diffs (across all folds)
| rank | fold | id | p_ts | p_py | absdiff |
|---:|---:|---|---:|---:|---:|
| 1 | 6 | rayyan-1178423369 | 0.671333 | 0.947203 | 0.275869 |
| 2 | 6 | rayyan-1178420090 | 0.635616 | 0.796457 | 0.160842 |
| 3 | 7 | rayyan-1178421403 | 0.713032 | 0.868902 | 0.155871 |
| 4 | 3 | rayyan-1178423508 | 0.655544 | 0.80644 | 0.150897 |
| 5 | 6 | rayyan-1178419078 | 0.719483 | 0.870242 | 0.150759 |
| 6 | 5 | rayyan-1178422285 | 0.739676 | 0.889665 | 0.149988 |
| 7 | 4 | rayyan-1178419978 | 0.729041 | 0.874746 | 0.145705 |
| 8 | 4 | rayyan-1178423436 | 0.809674 | 0.942321 | 0.132646 |
| 9 | 8 | rayyan-1178419338 | 0.682933 | 0.814193 | 0.131261 |
| 10 | 1 | rayyan-1178421017 | 0.868513 | 0.74153 | 0.126983 |

## Interpretation (quick)
- The disagreement is not explainable by tie-breaking alone when `top_scores/thr_score` differ and absdiff is non-trivial.
- Under ngram_range=(1,2), TS/Python diverge in feature/probability computations; likely suspects include tokenization/ngram generation, vocabulary ordering, or TF-IDF normalization.
