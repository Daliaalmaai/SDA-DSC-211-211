# Tamweel Lite — submission review / مراجعة التسليم

Review date: 8 October 2026. Student account: Daliaalmaai. Official student code: **211**, supplied by the learner.

The learner supplied the instructor's simplified submission notice. It takes precedence over older template requirements about template creation, Colab authorization, tags and SHA submission. Folder layout is allowed. One public repository is retained.

## Administrative requirements

| Requirement | Evidence / action |
|---|---|
| One public repository | `Daliaalmaai/SDA-DSC-211-211`; renamed existing repository, preserving history |
| README's ten requested elements | New overview includes project/course/account, code 211, objective, run instructions, tools, results, final model, threshold and limitations |
| One assembled code notebook | `FINAL_CODE_NOTEBOOK.ipynb`: readiness, Days 1–5 and technical final check; original source-cell IDs and hashes recorded |
| Individual notebooks 00–05 and 99 | `notebooks/`; 00–05 saved with outputs; 99 retained from its actual assembled execution |
| Decision, interpretation and model reports | `reports/DECISION_CARD.md`, `INTERPRETABILITY_REPORT.md`, `MODEL_CARD.md` |
| Ensemble decision and inference | `reports/ENSEMBLE_DECISION.md`, `tamweel/inference.py`, `scripts/replay_final.py`, `scripts/rebuild_final.py` |
| Final predictions | `submission/submission.csv`: 2,500 unique synthetic IDs in challenge order; probabilities and review decisions |
| Presentation | `presentation/final_presentation.pdf`: five slides with evidence, decision and limitations |
| Private submission | Learner must send the link and required identification through the approved private channel; no public Issue is a submission receipt |

## Technical evidence and grading coverage

| Rubric area | Evidence and interpretation |
|---|---|
| Baselines and boosting | Day 1 Logistic Regression/XGBoost/LightGBM comparison and learning curves; random teaching split is explicitly limited |
| Honest validation and Optuna | Day 2 forward folds, zero shared customers, mature training labels, training-only imputation, eight completed live tuning trials; no repeat search based on outer disappointment |
| Imbalance, cost and capacity | Day 3 unweighted/weighted/oversampled comparisons, threshold sweep, 10 FN + FP, period capacity and regional denominators |
| Interpretation, calibration and stability | Day 4 permutation importance, global/local SHAP and additivity, held-out calibration evaluation, bootstrap and local stability |
| Ensemble and final selection | Day 5 nested OOF, averaging/stacking comparison, predefined gate; KEEP SINGLE Logistic with mean fold AP 0.39166 |
| Final policy and reproducibility | Raw OOF threshold 0.16892161427109176; transported 0.12225843144286948; full challenge cap 300/2,500; saved model replay matches probabilities to 1e-12 and decisions exactly |
| Responsible use | Synthetic educational review; no automatic credit decision, no challenge performance claim, no fairness certification |
| Presentation and defence | Five-slide PDF is present; understanding and oral responses require learner participation and instructor judgment |

The previously checked repository snapshot passed all 100 final technical checks, including fresh isolated execution of readiness and Days 1–5. The assembled notebook completed all 60 code cells on free CPU without error outputs; its final-check section reported readiness. A technical PASS does not predict or award a rubric score.

## Findings that must remain visible

- The learner supplied code 211. The chosen repository name is `SDA-DSC-211-211`.
- Day 4's uncertainty review band exceeds capacity in two periods. This is a documented analytical finding, not an execution error; do not retune on those evaluation outcomes. Day 5 uses its separate frozen batch policy.
- Day 4 SHAP explains weighted LightGBM. It must not be presented as an explanation of the final Logistic model.
- Final sigmoid calibration-fit Brier/ECE worsened. The report states this; these fit diagnostics are not an independent test.
- Development OOF was used for selection; related temporal folds do not establish significance or universal superiority. Challenge labels are unavailable.
- Written responses were drafted with Codex assistance. Review their meaning and be able to defend them; the presence checker does not assess correctness or authorship.

## Privacy review

Source, notebook and output text were scanned for token prefixes, private contact details and forbidden credential filenames. Hash digit sequences and Python matrix multiplication are treated as false positives only after contextual inspection. Project IDs and customer records are synthetic. No authentication information is needed in notebooks. Public availability and final saved execution state are verified separately before completion.

This review maps evidence to requirements; it is not an instructor grade, submission receipt, or guarantee that every human-reviewed criterion earns full credit.
