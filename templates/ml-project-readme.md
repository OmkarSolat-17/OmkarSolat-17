# ML project README template

> Authoring guide: copy this into an ML project's README, replace the prompts with verified details, and delete this note. Do not publish placeholders, untested commands, or invented measurements. Omit optional sections rather than implying work is complete.

## Project name and summary

Describe the problem, intended user, input, and output in two sentences. State whether this is an experiment, prototype, or deployed application.

**Status:** What works today? What is still missing?

**Demo:** Link to a verified deployment or a repository-local screenshot/video with descriptive alt text. State if a demo needs particular hardware or local model files.

## Problem and scope

- What decision or task does this support?
- Why is ML appropriate? What simpler non-ML approach could work?
- What is explicitly out of scope?
- Which functionality is implemented versus planned?

## Approach

Explain the flow from raw input through preprocessing, model training, evaluation, and inference. A short text diagram is enough.

Describe why you selected the baseline and model, including important trade-offs. Mention any generated or adapted components and credit their sources.

## Data

Document:

- Dataset name, version, source URL, license, attribution, and access requirements.
- Download/preparation instructions and expected directory structure.
- Actual sample counts, classes, missing values, and meaningful imbalance.
- Train/validation/test split sizes and split unit: row, user, signer, session, or time.
- How duplicate or related samples are kept from leaking across splits.
- Which preprocessing steps are fitted on training data only.
- Personal/sensitive data handling and redistribution restrictions.

If data cannot be shared, explain how to request it or provide a clearly labeled synthetic example. Never imply synthetic-data results measure real-world performance.

## Reproduce locally

State the tested operating system, Python version, dependency versions, hardware, and expected runtime. Say whether a GPU is optional or required.

Include commands you have actually tested for:

1. Cloning the repository and entering its directory.
2. Creating and activating an isolated environment.
3. Installing dependencies from the project's dependency file.
4. Obtaining and preparing data using a configurable path.
5. Training the model with an explicit config and seed.
6. Evaluating a saved artifact on the intended split.
7. Running inference on one example.

Show expected output from a real run. Document required model files and label mappings, where to obtain them, and how their versions match the code. Do not require another developer to recreate your personal filesystem paths.

## Evaluation

Explain the baseline, metric definitions, evaluation split, and model-selection procedure before showing results.

Record each measured run with:

- Model and baseline configurations.
- Dataset version and split definition.
- Random seed(s), dependency versions, and code commit.
- Metric values, units, and the command used to generate them.
- Runtime/hardware when reporting latency or training cost.
- Variability across runs when measured; do not invent confidence intervals.

For recommenders, distinguish rating prediction from ranking and define K, candidate sampling, relevance, and seen-item filtering. For classifiers, include class-level performance and the confusion matrix rather than accuracy alone.

If no reliable evaluation exists yet, state **“Evaluation pending”** and describe the missing work instead of publishing a score.

## Error analysis and limitations

Describe actual inspected failures, the data conditions where performance degrades, and known biases. Include cold-start behavior, unsupported inputs, or distribution shift where relevant.

State intended use, out-of-scope use, and whether human review is needed. Health and accessibility prototypes must not imply clinical or interpreter-level reliability without evidence.

## Testing and quality checks

List real commands for tests, linting, and a small smoke run. Explain what they cover and what remains manual. Separate lightweight synthetic-data CI checks from expensive training or credential-dependent tests.

Useful checks include schema validation, train/test separation, deterministic ID mappings, preprocessing consistency, artifact loading, and inference output shape/range.

## Repository structure

Show the actual structure, with a brief purpose for key files and directories. Do not list modules that do not exist yet.

Keep secrets out of Git. Document how data and model artifacts are stored, versioned, and retrieved without committing large or restricted files.

## Roadmap

List a few concrete next steps with acceptance criteria. Separate planned features from completed ones. Link to issues if they exist.

## License and acknowledgments

Link to the actual code license after choosing one. Document separate dataset/model licenses and required citations. Credit tutorials, libraries, collaborators, and adapted code.

A public repository without a license is not automatically permission to reuse its contents.
