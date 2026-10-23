# GitHub improvement plan

Public-profile review: **23 October 2026**. This is a maintenance guide, not profile-facing copy.

## Scope and evidence

Reviewed the public account metadata, pinned repositories, default-branch file trees, and available READMEs for all nine public repositories. Also inspected the recommender's `main.py` and the sign-recognition project's `train.py` and `predict.py`.

This was a static review, not a successful execution of either ML project. No benchmark, deployment, or model-quality claim has been verified. External portfolio and social destinations were not availability-tested.

Sources: [account metadata](https://api.github.com/users/OmkarSolat-17), [public repositories](https://github.com/OmkarSolat-17?tab=repositories), and the repository/source links below. Findings are a point-in-time snapshot and should be rechecked after changes.

## What changed in this profile repository

- Replaced duplicated sections, embedded line-break-heavy formatting, and placeholder text with a concise profile.
- Prioritized the two ML implementations; explicitly labeled them as prototypes.
- Removed decorative statistics, trophies, quotes, and third-party badge dependencies.
- Removed unsupported project listings and broad cloud/framework badges that lacked evidence in the reviewed ML code.
- Kept existing professional contact details; did not invent a deployed portfolio, job history, metrics, or credentials.
- Added this plan and a reusable [ML project README template](../templates/ml-project-readme.md).

These edits do **not** update the live profile until the profile README reaches the profile repository's default branch. Account settings, repository metadata, pins, and other repositories were not changed.

## 1. Profile settings — quick wins

At review time, the public name, bio, website, and location fields were empty, and there were no pinned repositories.

Suggested settings, to review before applying:

| Field | Suggested value |
| :--- | :--- |
| Name | Omkar Solat |
| Bio | Computer Science student specializing in AI/ML. Building Python projects in recommendation systems and computer vision. |
| Website | Add the canonical portfolio URL only after verifying that the deployment works. A source repository is not a live demo. |
| Location | Add only the location you want public; do not infer it from your browsing location. |
| Social link | Use the LinkedIn URL already listed in the profile README. |

Use a clear, recognizable avatar. Keep contact details consistent across your README, LinkedIn, résumé, and portfolio. Add an availability statement only if it is accurate.

### Pin order

Start with three or four good repositories; there is no requirement to fill all six slots.

1. **Movie-Recommendation-System** — lead ML project once the evaluation and setup issues below are fixed.
2. **Sign-Language-Recognition-System** — computer vision project once dataset and inference instructions are documented.
3. **portfolio** — a single canonical portfolio, after adding a screenshot and verified demo link.
4. **MyBloggy** — supporting web-development work, explicitly a static demo.

Until the ML repairs are complete, keep their prototype status visible. Do not pin README-only projects as implemented applications. Choose pins using **Customize your pins** on your GitHub profile.

## 2. Repository-by-repository cleanup

All nine repositories had no topics and no GitHub-detected license at review time. License detection can miss nonstandard files: check ownership and third-party terms before selecting a license. Dataset and model licenses are separate from your code license.

The descriptions and topics below are proposals, not applied changes.

| Repository | Observed state | Suggested description | Suggested topics |
| :--- | :--- | :--- | :--- |
| [OmkarSolat-17](https://github.com/OmkarSolat-17/OmkarSolat-17) | Profile README; rewritten in this branch | Profile and project overview — Computer Science student focused on AI and machine learning. | `github-profile`, `profile-readme` |
| [Movie-Recommendation-System](https://github.com/OmkarSolat-17/Movie-Recommendation-System) | One Python script; brief README; no dependency file or tests | MovieLens recommendation prototype exploring TF-IDF, SVD, and autoencoder user embeddings in Python. | `python`, `recommender-system`, `movielens`, `scikit-learn`, `tensorflow` |
| [Sign-Language-Recognition-System](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System) | Training and webcam scripts; no dependency file, dataset instructions, or tests | Hand-sign image classification prototype using a Keras CNN, OpenCV, and MediaPipe webcam detection. | `python`, `computer-vision`, `tensorflow`, `opencv`, `mediapipe` |
| [portfolio](https://github.com/OmkarSolat-17/portfolio) | HTML, CSS, and JavaScript; two-line README | Personal portfolio website built with HTML, CSS, and JavaScript. | `portfolio`, `html`, `css`, `javascript` |
| [MyBloggy](https://github.com/OmkarSolat-17/MyBloggy) | Static site; detailed README.txt; browser-local accounts and posts | Static blogging demo with search, theme switching, and browser-local posts using HTML, CSS, and JavaScript. | `javascript`, `html`, `css`, `blog`, `learning-project` |
| [dynamic-web-page](https://github.com/OmkarSolat-17/dynamic-web-page) | Small HTML/CSS/JS exercise; placeholder README | A small front-end practice project using HTML, CSS, and JavaScript. | `html`, `css`, `javascript`, `learning-project` |
| [omkar-solat-portfolio](https://github.com/OmkarSolat-17/omkar-solat-portfolio) | Exported app with TypeScript front-end source; no README returned by the API | Portfolio application exported from Caffeine, with a TypeScript front end. | `portfolio`, `typescript` |
| [BloodBridge](https://github.com/OmkarSolat-17/BloodBridge) | Default branch contains only a two-line README | BloodBridge — project planning repository; implementation not yet published. | `project-planning` |
| [Hospital-Management-System](https://github.com/OmkarSolat-17/Hospital-Management-System) | Default branch contains only a README describing a Tkinter/MySQL application | Hospital management project overview; implementation not yet published in this repository. | `project-planning` |

### Supporting repository actions

- **portfolio:** add purpose, local run instructions, a screenshot, and a working deployment URL. Review all career and project claims for accuracy.
- **omkar-solat-portfolio:** choose whether this or `portfolio` is canonical. Document what was generated and what you changed. If superseded, link to the canonical version and consider archiving only after checking for unique work. Do not delete it solely to simplify the profile.
- **MyBloggy:** convert `README.txt` into a properly rendered `README.md`; preserve the useful explanation. Keep the warning that browser-local passwords are demo-only, and use fake credentials. The marks predictor is a formula, not ML. Do not market it as an AI model or deploy the login as real authentication.
- **dynamic-web-page:** replace the placeholder with the exercise's purpose, a screenshot, and run instructions. Keep it unpinned rather than hiding honest learning history.
- **BloodBridge:** fix the description typo and add problem definition, scope, milestones, and implementation status. Do not claim an implemented AI system or medical reliability.
- **Hospital-Management-System:** publish the actual implementation if you own it and it is ready, or label the repository as an overview. Before publishing, remove database credentials and patient data; use synthetic fixtures and provide a schema.

## 3. Highest priority: make the recommender credible

Source reviewed: [`main.py`](https://github.com/OmkarSolat-17/Movie-Recommendation-System/blob/HEAD/main.py).

### Correctness before presentation

- **Fix evaluation leakage:** `collaborative_filtering_svd` transforms `test_ratings` and evaluates reconstruction of those same observed test entries. Instead, infer from training interactions only, then score predictions at held-out user-item pairs. Held-out values must not enter the prediction input.
- **Train the autoencoder on training data only:** it currently receives the full ratings matrix. Keep validation/test interactions out of training and hyperparameter selection.
- **Separate user IDs from movie IDs:** nearest neighbors are computed over user embeddings, but those neighbor IDs are compared against movie IDs in `emb_score`. Aggregate neighbor preferences into movie scores, or build actual item embeddings.
- **Use explicit ID mappings:** replace `user_id - 1` and `movie_id - 1` assumptions with lookup tables. Align user rows and item columns consistently across all matrices.
- **Name metrics correctly:** `evaluate_model` labels the SVD reconstruction result as “Overall Hybrid RMSE”; it does not evaluate the final hybrid ranking. Report rating-prediction and ranking metrics separately.
- **Make hybrid weights meaningful:** calibrate or normalize component scores before combining them. Select weights on validation data, not the test set.

### Recommender acceptance criteria

- [ ] Replace the machine-specific Windows data path with a CLI argument or config setting.
- [ ] Document the MovieLens 100K source, version, usage terms, expected files, and download steps. Do not silently redistribute it.
- [ ] Add a tested Python version and dependency file; verify installation in a clean environment.
- [ ] Add a popularity baseline using training interactions only.
- [ ] Define the split protocol, relevance threshold, candidate set, and treatment of seen items and cold-start users.
- [ ] Report Recall@K and NDCG@K for top-K recommendations; use RMSE only for an explicitly defined rating-prediction task.
- [ ] Save real results with the seed, configuration, dependency versions, and commit used.
- [ ] Test ID alignment, exclusion of seen items, unknown users, empty history, and absence of held-out interactions from training input.
- [ ] Add a small synthetic-data smoke test to CI; keep dataset download and expensive training out of routine CI.
- [ ] Add an example recommendation output and explain one failure case.

Do not publish a “hybrid improvement” number until a corrected evaluation actually supports it.

## 4. Make the vision project reproducible and precise

Sources reviewed: [`train.py`](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System/blob/HEAD/train.py) and [`predict.py`](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System/blob/HEAD/predict.py).

### Correctness and scope

- Describe it as classification of supported hand-sign images, not general sign-language translation. The scripts do not establish sentence-level or temporal language understanding.
- Document the dataset source, license, sign language, labels, collection conditions, and permitted uses. These cannot be determined from the scripts alone.
- Save the class-to-index mapping with the trained model. Inference currently re-reads a local training directory, making deployment depend on that directory and its contents.
- Replace hardcoded Windows paths with configurable paths; validate missing directories and model files with actionable errors.
- Check failed image reads before resizing; clamp hand bounding boxes to frame bounds before cropping.
- Make training and inference preprocessing consistent, including hand crops, image size, channel order, and scaling.
- Use signer/session-independent evaluation when those identities are available; random image splits may leak similar examples. If provenance is unavailable, state the limitation instead of claiming signer independence.
- Keep a final test set separate from the validation set currently passed to `model.fit`.

### Vision project acceptance criteria

- [ ] Specify tested Python, TensorFlow, OpenCV, and MediaPipe versions, including compatibility with `mp.solutions.hands`.
- [ ] Document training, model export, label metadata, and webcam inference commands verified on a clean setup.
- [ ] Report macro F1, per-class precision/recall, and a confusion matrix on the final held-out set.
- [ ] Measure inference latency on named hardware, distinguishing model time from full camera-pipeline time.
- [ ] Add tests for label consistency, preprocessing shape/range, failed image reads, and empty or out-of-bounds crops.
- [ ] Include a short consented demo and discuss lighting, occlusion, backgrounds, handedness, and unsupported signs.
- [ ] Explain confidence behavior; if a rejection threshold is added, calibrate it on validation data and document its limitations.
- [ ] State that the prototype is not a replacement for an interpreter or an accessibility-critical service.

## 5. A practical four-week sequence

| Week | Focus | Done when |
| :--- | :--- | :--- |
| 1 | Clear profile and honest repository metadata | Profile README published; bio filled; descriptions/topics reviewed; canonical portfolio chosen; placeholder-only projects labeled. |
| 2 | Recommender reliability | Clean setup works; leakage and ID bugs fixed; baseline and held-out ranking evaluation documented. |
| 3 | Vision reliability | Dataset instructions, portable paths, saved labels, preprocessing checks, and honest held-out evaluation documented. |
| 4 | Presentation and delivery | Best repos have screenshots/demos, tests and CI, reviewed licenses, limitations, and a tagged release where appropriate. |

This sequence is a suggested plan, not a claim about completed work. Two reproducible, well-explained ML projects are more persuasive than many unfinished “AI” repositories.

## 6. Standard for a flagship ML repository

Use the [README template](../templates/ml-project-readme.md) as a checklist, not a reason to invent missing evidence.

- A precise problem statement and honest implementation status.
- Runnable setup and a minimal example from a clean clone.
- Dataset provenance, rights, split strategy, and leakage controls.
- A simple baseline before a complex model.
- Measured results with a reproducible evaluation command.
- Tests for data validation and inference behavior; CI that runs them.
- A demo or screenshot that matches the current code.
- Failure analysis, intended use, and out-of-scope uses.
- Secrets and personal data excluded; large datasets/checkpoints stored outside Git unless justified and permitted.
- A license you deliberately selected after reviewing ownership and dependencies.

Avoid fabricated contribution activity, copied metrics, inflated expertise badges, and “production-ready” claims without operational evidence. Good engineering decisions and reproducible evidence should do the selling.

## Publishing this pass

1. Review the profile wording, listed skills, and contact details for accuracy.
2. Merge the reviewed changes from this working branch into the profile repository's default branch through a pull request.
3. Confirm the README renders on your public profile on desktop and mobile.
4. Apply the reviewed profile settings, descriptions, topics, and pins separately.
5. Implement the two ML repair checklists in their own repositories; this profile-only change does not fix their code.
