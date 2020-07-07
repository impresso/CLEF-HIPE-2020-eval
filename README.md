# CLEF-HIPE-2020 Evaluation Toolkit

To reproduce the results and plots in the paper, clone this repository with its submodules and run the provided Makefile with:

```bash
git clone --recursive https://github.com/impresso/CLEF-HIPE-2020-eval
cd CLEF-HIPE-2020-eval
make eval-full VERSION=v1.3 RELEASE_DIR=data/release
```



This runs the entire evaluation workflow that builds on the submissions, gold standards and a historical mapping resource only. Original submissions can be found in `systems/submitted/`. To account for inconsistencies in data annotation, the evaluation is performed on the time-normalized submissions `systems/time-normalized` rather than the original files where all time mentions are linked to NIL. The historically normalized submissions can be found in `systems/histo-normalized` that are evaluated against a similar normalized version of the gold standard in fuzzy EL. The historical mappings themselves are provided with `historico-fuzzy-QID-mapping-ID-mapping.tsv`

The individual results per system run and task may be found in `evaluation-results/system-evaluations`, while the overall ranking per task and evaluation regime may be found in `evaluation-results/system-rankings`. As there are many records per file, you may want to use `grep` to find relevant results:

```bash
# EXAMPLE
# get overall ranking for NERC Coarse (across time and noise)
grep -rP "NE-COARSE-LIT-micro-fuzzy-TIME-ALL-LED-ALL\tALL" ranking-de-coarse-micro-fuzzy-all.tsv
```

The plots shown in the paper may be found in `evaluation-results/robustness`.



