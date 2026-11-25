# Independent QC review — integral-homology-audit

**Independent findings summary.** This is a mathematically coherent exact-computation package: the instruction specifies chain-complex conventions, full Smith witnesses and integral homology; the reference tracks unimodular operations; the verifier checks exact identities and derives torsion on small inputs, then exercises basis-changed controls. Harbor evidence includes successful Oracle runs, no-op/rank-only failures and oversized/failed development cases. Direct trajectory metadata confirms zero AI-model trials, so success-rate/difficulty calibration is NOT TESTED. The author-experience placeholder remains. Current configuration now sets no-network and verifier requirements pin pytest 8.4.1 with CTRF; no Harbor run after these 2026-11-25 harness changes is present. The supplied complexes are synthetic abstract fixtures rather than sourced research data. Separate verifier copy design is visible, but actual image isolation was not audited.

**Overall QC verdict: INCOMPLETE.** Required evidence/checks remain unresolved: static `task-fields` and rubric `task_toml_schema` because author experience is a placeholder (`task.toml:24`); `instruction-similarity`, `novel`, and `ctrf_reporting` lack completed evidence; and no independent model trials exist. Under the master checklist's final rule, unresolved required results make the overall result Incomplete (`QC-CHECKLIST.md`, “How QC decides the verdict”).

**Scope and evidence convention.** Package source and `jobs/integral-homology-audit/` Harbor evidence reviewed. Oracle validations and no-op/rank-only controls are not AI-model trials. The trajectory file explicitly records zero completed trials. Creator-authored audits were read only after this independent assessment and corroborate several limitations (synthetic data, no model runs, incomplete experience metadata, no post-build isolation audit); this report makes independent verdicts. Master checklist retained unchanged.

## Static checks (29)

| ID | Verdict | Independent evidence / remediation |
|---|---|---|
| `entry-files` | PASS | `instruction.md:1-53`, `task.toml:1-47`, `environment/Dockerfile:1-4`, `solution/solve.sh:1-5`, `tests/test.sh:1-14` exist. |
| `config-fields` | PASS | Manifest field/table structure is explicit (`task.toml:3-47`). |
| `task-fields` | WARNING | Required author experience remains intentionally unresolved in `task.toml:24`. Preserve the non-claim until the author supplies a truthful statement, then rerun publication metadata review. |
| `task-path` | PASS | Manifest `domain`/`field` at `task.toml:19-21` match directory `mathematical-sciences/applied-mathematics`. |
| `task-structure` | PASS | Root files and environment, solution, tests, authoring directories in expected locations. |
| `task-slug` | PASS | `integral-homology-audit` uses valid lowercase hyphenated identifier length. |
| `task-readme` | WARNING | README is accurate and useful (`README.md:3-21`) but lacks managed metadata header; add/regenerate canonical header if required by publisher profile. |
| `canary` | PASS | Required local canary appears in task, instruction, reference, verifier and authoring files (for example `task.toml:2`, `instruction.md:1`, `solution/solve.py:1`, `tests/test_outputs.py:1`). |
| `task-absolute-path` | PASS | Input, solver, result and CLI paths are absolute in instruction (`instruction.md:5,20,47-53`). |
| `instruction-suffix` | PASS | 28,800-second closing statement (`instruction.md:53`) matches `agent.timeout_sec=28800` (`task.toml:38-39`). |
| `instruction-similarity` | NOT TESTED | Pinned task-collection comparison output is not in package or Harbor run evidence; run the prescribed similarity checker. |
| `test-file-references` | PASS | `/app/solve.py` and `/app/results/homology.json` are both instructed (`instruction.md:20,47-53`) and declared artifacts (`task.toml:4`). |
| `dockerfile-references` | PASS | Solver `COPY data/` resolves to `environment/data/` (`environment/Dockerfile:4`); verifier copies named files present in `tests/` (`tests/Dockerfile:4-9`). |
| `dockerfile-sanity` | PASS | Slim image and simple COPY/RUN structure (`environment/Dockerfile:2-4`, `tests/Dockerfile:2-10`). |
| `dockerfile-platform` | PASS | Neither Dockerfile hardcodes architecture (`environment/Dockerfile:2`, `tests/Dockerfile:2`). |
| `allow-internet` | PASS | Solver and verifier declare `network_mode = "no-network"` (`task.toml:32,47`), matching the no-network instruction (`instruction.md:20`). |
| `separate-verifier` | PASS | Separate no-network verifier config (`task.toml:27-36`) and hidden/public inputs copied only in verifier image (`tests/Dockerfile:6-9`). |
| `compose-host-binds` | PASS | No Docker Compose host directory bind present in package. |
| `task-timeout` | PASS | Agent timeout 28,800 sec, verifier 300 sec, build 600 sec (`task.toml:27-42`); test subprocess caps candidate at 180 sec (`tests/test_outputs.py:171-178`). |
| `gpu-types` | PASS | Both environment profiles request zero GPUs (`task.toml:31-46`). |
| `task-resources` | PASS | 2 CPUs, 4 GB RAM, 10 GB storage (`task.toml:41-47`) match exact integer reductions and 28x28 dense tests. |
| `verifier-resources` | PASS | Separate verifier also declares 2 CPUs/4 GB/10 GB (`task.toml:31-36`), consistent with workload. |
| `nproc` | PASS | No bare `nproc` process-count call in source/scripts. |
| `verifier-tooling-baked` | PASS | pytest and SymPy installed in verifier image at build (`tests/Dockerfile:4-5`); grading script only invokes pytest. |
| `trial-network-fetch` | PASS | Runtime scripts do not fetch data/network (`solution/solve.sh:1-5`, `tests/test.sh:1-14`). |
| `pip-pinning` | PASS | Verifier dependencies pinned in `tests/requirements.txt:2-3`; solver uses standard library only (`solution/solve.py:1-10`). |
| `pytest-version` | PASS | `tests/requirements.txt:2-3` pins `pytest==8.4.1` and `pytest-json-ctrf==0.3.5`, as required; the updated environment has not yet been run. |
| `test-sh-sanity` | PASS | `tests/test.sh:3-14` captures pytest result and writes binary reward. |
| `binary-reward` | PASS | Only `1` or `0` is written (`tests/test.sh:8-12`). |

## LLM rubric checks (38)

| ID | Verdict | Independent evidence / remediation |
|---|---|---|
| `well_specified` | PASS | Chain-complex conventions, exact output schema and witness conditions explicit (`instruction.md:5-20,22-45`). |
| `test_instruction_alignment` | PASS | Verifier checks all named outputs, equations, determinants, divisibility and generated bases (`tests/test_outputs.py:76-123,125-195`). |
| `instruction_clarity` | PASS | Defines matrix dimensions, chain identity, homology groups and invocation (`instruction.md:5-20,45-53`). |
| `structured_data_schema` | PASS | JSON schema and dimensions detailed (`instruction.md:22-45`); exact verifier schema (`tests/test_outputs.py:76-104`). |
| `typos` | WARNING | Math text contains literal TeX-like parenthesized variables and a mojibake `Â±` in instruction line 45; fix notation/encoding for professional clarity. |
| `hint_discoverability` | PASS | Inputs and allowed dependencies are explicit; no hidden task-specific hint required (`instruction.md:5-20`). |
| `scientifically_grounded` | WARNING | Integral homology is an established computational topology problem, but data are synthetic abstract chain complexes; tie task to a concrete topological/research question or document why these fixtures reflect a real workflow (`README.md:5-13`, `authoring/proposal_rubric_review.md` section). |
| `scope` | PASS | Exact algebraic topology fits mathematical-sciences/applied-mathematics (`task.toml:19-22`). |
| `essential_difficulty` | WARNING | Exact torsion and certified Smith witnesses are substantive (`instruction.md:9-20`), but no model/expert performance evidence exists; do not claim calibrated benchmark difficulty. |
| `novel` | WARNING | The originality assessment and report explicitly say **qualitative only**: full reference checkout/data absent; text, code and data comparisons not run; numeric similarity null (`authoring/originality_assessment.md` sections “Comparison scope and limits”/“Publication follow-up”; `authoring/plagiarism/reports/plagiarism_report.md` opening and final paragraphs; `authoring/plagiarism/reports/plagiarism_report.json`: `reference_repository_checkout_available=false`, comparisons `not_run`). `compare.py` is only a supplied 5-gram lexical tool and has no recorded comparison output. Current conceptual separation from three task summaries supports a favorable preliminary assessment, but cannot establish collection-wide novelty. Keep WARNING pending comparisons against permitted reference snapshots and document exact source commits/results. |
| `agentic` | PASS | Must inspect JSON, implement exact matrix algorithm and test certificates (`instruction.md:20,47-53`; solution code performs operations). |
| `verifiable` | PASS | Exact integer products and unimodular determinants check certificates (`tests/test_outputs.py:89-104`). |
| `solvable` | PASS | Final Oracle trial passes twice and solution is available (`jobs/integral-homology-audit/2026-11-23__18-43-51/result.json`); reference code derives output from input. |
| `outcome_verified` | PASS | Any valid witness accepted by exact products/determinants; independent minors recompute small-case torsion (`tests/test_outputs.py:34-54,95-118`). |
| `functional_verification` | PASS | Verifier runs candidate on public and random basis-changed cases, checks actual result (`tests/test_outputs.py:171-195`). |
| `ground_truth_provenance` | WARNING | Fixtures and verifier logic are inspectable, but no cited external source for input complexes; document generation/derivation and intended mathematical interpretation. |
| `graded_instances_discriminate` | PASS | No-op/rank-only controls fail, Oracle passes; controls recorded under `jobs/integral-homology-audit/2026-11-23__17-55-37` and `17-57-30`; coverage includes nontrivial torsion (`tests/test_outputs.py:198-203`). |
| `solution_quality` | PASS | Reference computes reductions with tracked integer row/column ops and derives groups from ranks (`solution/solve.py:46-131,173-201`). |
| `do_not_modify_enforced` | PASS | No protected input file rule stated (`instruction.md:1-53`). |
| `deterministic_reproducible` | PASS | Final Oracle 2/2 reward 1 and matching output hashes documented by direct evidence in `jobs/integral-homology-audit/2026-11-23__18-43-51/result.json`; deterministic seeded transformations (`tests/test_outputs.py:125-149`). |
| `separate_verifier_configured` | PASS | Separate no-network verifier (`task.toml:27-36`) with independent verifier image and copied cases (`tests/Dockerfile:4-10`). |
| `verifier_execution_isolation` | WARNING | Source COPY structure excludes hidden inputs from agent image, but no post-build filesystem audit is in Harbor record (`authoring/reports/harbor_validation.md:24-28`); perform and retain image audit. |
| `anti_cheat_robustness` | PASS | Candidate is rerun on seeded basis-changed public/hidden complexes and a larger dense map (`tests/test_outputs.py:125-195`); no-op and rank-only controls fail. |
| `task_security` | PASS | No host/secret access evident in inspected files; solver and verifier now declare no-network (`task.toml:32,47`). Post-build image audit remains open under `verifier_execution_isolation`. |
| `resource_configuration` | PASS | 2 CPU/4 GB allocations and 180-second subprocess limit are explicit (`task.toml:31-47`, `tests/test_outputs.py:171-178`); final 28x28 run passed. |
| `task_toml_schema` | WARNING | Manifest parses and has expected naming/domain fields (`task.toml:6-25`), but required author experience is an unresolved placeholder (`task.toml:24`). Do not pass before the author supplies a truthful value. |
| `environment_hygiene` | PASS | Agent image copies only public chain-complex input, no test files (`environment/Dockerfile:2-4`); reference scripts are task artifacts, not baked in image. |
| `artifact_efficiency` | PASS | Declared artifacts match requested solver/output (`task.toml:4`, `instruction.md:20,47-53`); result JSON derives from input. |
| `ctrf_reporting` | NOT TESTED | Updated script invokes pytest with `--ctrf /logs/verifier/ctrf.json` (`tests/test.sh:3-14`), but all extant jobs predate this edit and no CTRF output is available. Run the current verifier and inspect its per-test report. |
| `task_authoring_dir` | PASS | Proposal, provenance, reports, controls and plagiarism material are under `authoring/`; runtime source/data in package dirs. |
| `no_extraneous_files` | PASS | Public/hidden cases, coverage/research/audit documents and negative controls each support the stated task/review. |
| `reviewable` | PASS | Chain identities, witness format and homology formula are documented (`instruction.md:5-20`); checker has independently readable derivation (`tests/test_outputs.py:30-73`). |
| `difficulty_explanation_quality` | WARNING | Proposal review names exact torsion/witness challenges but rates difficulty uncertain and notes no human/model study; see `authoring/proposal_rubric_review.md` and trajectory metadata. |
| `solution_explanation_quality` | PASS | Reference explanation and implementation correspond (`README.md:5-13`, `solution/solve.py:46-131,173-201`). |
| `verification_explanation_quality` | PASS | README describes independent torsion/certificate checks (`README.md:5`) and verifier source implements them (`tests/test_outputs.py:34-54,89-123`). Calibration study is absent, but alternative algorithms/certificates are accepted. |
| `category_and_tags` | PASS | Algebraic topology, integral homology, SNF and exact computation accurately described (`task.toml:19-22`). |
| `task_name` | PASS | `integral-homology-audit` is descriptive and manifest name matches (`task.toml:7`). |
| `task_readme` | PASS | README gives task summary, run/output details and Harbor commands (`README.md:3-21`); managed header is not needed to understand this content. |

### Harbor evidence interpretation

The current pytest/CTRF requirements and startup-script revisions are dated 2026-11-25; recorded jobs date 2026-11-23. Previous Oracle/control results do not verify the current test image or CTRF output.

- `authoring/trajectories/trajectory_summary.json:3-11` states `status: not_run`, `requested_trials: 8`, `completed_trials: 0`, `runs: []`. Thus all independent-model trial, observed success-rate, and agent difficulty calibration claims are **NOT TESTED**.
- Oracle validations: final `jobs/integral-homology-audit/2026-11-23__18-43-51/result.json` reports 2/2 reward 1.0; it is explicitly `oracle__adhoc`, not model.
- Controls: `17-55-37` no-op got reward 0; `17-57-30` rank-only got reward 0. These demonstrate discrimination against those controls only.
- Development/failure evidence includes early missing-reward run `17-51-55`, corrected fixture failure `17-53-30`, and timeout/engine issue `18-02-18` / `18-34-46`, summarized with paths in `authoring/reports/harbor_validation.md:20-22`. The final task changed hidden dimensions and passed, but this history is not model calibration.

### Check-report evidence and workspace note

- `jobs/2026-11-23__17-50-21/check_report.json` and `jobs/2026-11-23__17-50-44/check_report.json` contain empty `checks` objects and a Docker API permission failure before checks ran. These are **not** successful static/rubric reports and cannot settle any listed check.
- A separate workspace-root `task.toml` exists and names another `enzyme-kinetics-fit` configuration. It is outside the two requested package directories and was not used as evidence for either task review. Confirm intended packaging excludes or resolves this duplicate before publishing the workspace.


