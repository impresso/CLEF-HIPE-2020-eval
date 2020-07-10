# CLEF-HIPE-2020 Evaluation Toolkit

This repository contains the necessary material for replicating the results of the [CLEF-HIPE-2020 shared task](https://impresso.github.io/CLEF-HIPE-2020/) on NE processing on historical newspapers, namely:
- the scorer ([CLEF-HIPE-2020-scorer](https://github.com/impresso/CLEF-HIPE-2020-scorer) as a submodule);
- the submitted system responses;
- the historical mapping resource used for the relaxed EL evaluation setting (also in the scorer submodule);
- a makefile to run the whole evaluation process.

### How-To

To reproduce the results and the plots of the overview paper (cf.ref below), clone this repository with its submodules and run the Makefile:

```bash
git clone --recursive https://github.com/impresso/CLEF-HIPE-2020-eval
cd CLEF-HIPE-2020-eval
make eval-full VERSION=v1.3 RELEASE_DIR=data/release
```

This runs the full evaluation workflow based on systems' submissions, gold standards and the historical mapping resource. 

Original submissions can be found in `systems/submitted/`. 

The EL evaluation is run on the date-normalized submissions, where all date mentions are linked to NIL (the date type is not part of EL evaluation). The date-normalized versions can be found in `systems/time-normalized`.

The EL fuzzy evaluation is run on the histo-normalized submissions, where all QID are completed with historically related entities. The histo-normalized submissions can be found in `systems/histo-normalized` and the historical mappings corresponds to `historico-fuzzy-QID-mapping-ID-mapping.tsv`


The individual results per system run and task can be found in `evaluation-results/system-evaluations`, while the overall ranking per task and evaluation regime (strict vs fuzzy) may be found in `evaluation-results/system-rankings`. As there are many records per file, you may want to use `grep` to find relevant results:

```bash
# example: get overall ranking for NERC Coarse (across time and noise)
grep -rP "NE-COARSE-LIT-micro-fuzzy-TIME-ALL-LED-ALL\tALL" ranking-de-coarse-micro-fuzzy-all.tsv
```

The plots shown in the paper may be found in `evaluation-results/robustness`.

While the CRF baseline for NERC is trained during the evaluation workflow, the Aida baseline for EL is simply added to `systems/submitted/`.

### Additional links
- [official results](https://github.com/impresso/CLEF-HIPE-2020/blob/master/evaluation-results/ranking_summary_final.md)
- [data](https://github.com/impresso/CLEF-HIPE-2020/tree/master/data)

### References

**Participant teams Working Notes paper**

```
To appear in September 2020 in:
CLEF 2020 Working Notes. Working Notes of CLEF 2020 - Conference and Labs of the Evaluation Forum.
Editors: Linda Cappellato, Carsten Eickhoff, Nicola Ferro, Aurélie Névéol.
(link will be updated in due time).
```

**LNCS Shared Task Condensed Overview paper**

```
To appear in September 2020:
'Overview of CLEF HIPE 2020: Named Entity Recognition and Linking on Historical Newspapers'. Maud Ehrmann, Matteo Romanello, Alex Flückiger and Simon Clematide.
In: Experimental IR Meets Multilinguality, Multimodality, and Interaction. Proceedings of the 11th International Conference of the CLEF Association (CLEF 2020).
Editors: Avi Arampatzis, Evangelos Kanoulas, Theodora Tsikrika, Stefanos Vrochidis, Hideo Joho, Christina Lioma, Carsten Eickhoff, Aurélie Névéol, Linda Cappellato, Nicola Ferro.
Springer, LNCS 12260.
```

**CEUR Shared Task Extended Overview paper**
```
To appear in September 2020:
'Extended Overview of CLEF HIPE 2020: Named Entity Processing on Historical Newspapers'. Maud Ehrmann, Matteo Romanello, Alex Flückiger and Simon Clematide.
In: CLEF 2020 Working Notes. Working Notes of CLEF 2020 - Conference and Labs of the Evaluation Forum.
Editors: Linda Cappellato, Carsten Eickhoff, Nicola Ferro, Aurélie Névéol.
```



