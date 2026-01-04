# CQ1 parameter sweep: stop_words = None

## Summary
Disable stop words on both TS and Python baselines and re-run CQ1 10-fold comparison.

## Changes
- TS: experiments/asreview/src/text.ts
  - default stopWords: "english" -> null
- Python: experiments/asreview/baseline.py, experiments/asreview/cv_baseline.py
  - Tfidf(stop_words="english") -> Tfidf()

## Result (CQ1, k=10, seed=42)
- top100 ID overlap: mean=1.0, min=1.0, max=1.0, perfect=10/10

## Commands
python experiments/asreview/make_folds.py --dataset cq1 --k 10 --seed 42
npx ts-node --project experiments/asreview/tsconfig.json experiments/asreview/src/cv.ts --dataset cq1
python experiments/asreview/cv_baseline.py --dataset cq1
python experiments/asreview/compare_cv.py --dataset cq1