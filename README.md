# Hi, I'm Omkar Solat

Computer Science student · Building toward AI/ML engineering

I build Python projects in **recommendation systems** and **computer vision**, with a focus on turning experiments into understandable, reproducible software. Alongside ML, I'm developing my foundations in algorithms, databases, and web development.

My goal: take a problem from data exploration to a useful application—with clear evaluation, tests, and honest limitations.

[![LinkedIn: Omkar Solat](https://img.shields.io/badge/LinkedIn-Omkar%20Solat-0A66C2?style=flat-square)](https://www.linkedin.com/in/omkar-solat-os17)
[![Email Omkar](https://img.shields.io/badge/Email-Contact%20me-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:omkarsolat2007@gmail.com)
[![Portfolio source on GitHub](https://img.shields.io/badge/Portfolio-Source%20code-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/OmkarSolat-17/portfolio)

**Explore:** [Projects](#selected-projects) · [Technical foundations](#technical-foundations) · [Learning priorities](#learning-priorities) · [Collaborate](#lets-connect)

---

## Selected projects

| Project | Focus | Start here |
| :--- | :--- | :--- |
| [Movie Recommendation System](https://github.com/OmkarSolat-17/Movie-Recommendation-System) | Offline recommendation experiments and evaluation | [Setup & synthetic demo](https://github.com/OmkarSolat-17/Movie-Recommendation-System#quick-start) |
| [Sign Language Recognition System](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System) | Hand-sign image classification and local inference | [Dataset guide](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System/blob/main/docs/dataset.md) |
| [MyBloggy](https://github.com/OmkarSolat-17/MyBloggy) | Front-end interfaces and browser-local state | [Project guide](https://github.com/OmkarSolat-17/MyBloggy/blob/main/README.txt) |

### Movie Recommendation System

**Question:** How do simple baselines, collaborative filtering, and genre-based recommendations compare under the same evaluation protocol?

- **Approach:** global/item means, popularity, SVD, genre-based TF-IDF, and a weighted hybrid on MovieLens 100K-format data. Rating-derived model state is fitted on training interactions only.
- **Engineering:** packaged Python CLI, configurable data paths, explicit user/movie ID mappings, deterministic splits, JSON reports, regression tests, and a CI workflow.
- **Evaluation:** RMSE/MAE for rating predictors; Precision@K, Recall@K, and NDCG@K for full-catalog ranking excluding training-seen items.
- **Try it:** the repository includes a synthetic demo that needs no dataset download. Synthetic results are smoke tests, **not MovieLens benchmarks**.
- **Scope:** a CPU-based offline experiment suite, not a deployed recommendation service. No quality improvement over baselines is claimed here.

[Source & setup](https://github.com/OmkarSolat-17/Movie-Recommendation-System) · [Evaluation protocol](https://github.com/OmkarSolat-17/Movie-Recommendation-System#evaluation-protocol) · [Validation notes](https://github.com/OmkarSolat-17/Movie-Recommendation-System/blob/main/docs/validation.md)

### Sign Language Recognition System

**Question:** How can a CNN classify a defined set of hand-sign images and expose predictions through a local interface?

- **Approach:** TensorFlow/Keras image classification, with MediaPipe hand detection and OpenCV for webcam/video input; single-image prediction is also supported.
- **Engineering:** configurable training and prediction commands, saved label mappings, confidence-aware output, input validation, tests, and a CI workflow.
- **Try it:** supply a labeled image dataset, train a model, and use the matching model and labels for prediction. **No dataset or pretrained model is bundled.**
- **Scope:** recognition of the classes in the training dataset—not general sign-language translation. Accuracy and generalization depend on the data and require evaluation on unseen signers and conditions.

[Source & setup](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System) · [Dataset requirements](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System/blob/main/docs/dataset.md) · [Architecture](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System/blob/main/docs/architecture.md)

### MyBloggy

A static blogging interface built with **HTML, CSS, and JavaScript**, with search, category filters, theme switching, and browser-local posts.

- **Practice areas:** UI behavior, client-side state, and multi-page navigation.
- **Scope:** a front-end learning demo. Browser-local accounts and storage are not secure production authentication or a backend service.

[Source & project guide](https://github.com/OmkarSolat-17/MyBloggy)

## Technical foundations

*Tools used in my learning projects—not certifications or proficiency ratings.*

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/OmkarSolat-17/Movie-Recommendation-System)
[![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)](https://github.com/OmkarSolat-17/Movie-Recommendation-System)
[![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)](https://github.com/OmkarSolat-17/Movie-Recommendation-System)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)](https://github.com/OmkarSolat-17/Movie-Recommendation-System)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System)
[![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)](https://github.com/OmkarSolat-17/Sign-Language-Recognition-System)

| Area | Tools and practice |
| :--- | :--- |
| Recommendation systems | NumPy, pandas, scikit-learn, SVD, TF-IDF, offline ranking metrics |
| Computer vision | TensorFlow/Keras, OpenCV, MediaPipe, CNN image classification |
| Reproducible Python | CLI configuration, dependency files, pytest, Ruff, GitHub Actions |
| Visualization | Matplotlib |
| Programming foundations | Python, C, Java, JavaScript, SQL |
| Web and data tools | HTML, CSS, Git, GitHub, MySQL |

## Learning priorities

I'm building on the project tooling already in place, with the next emphasis on evidence and generalization:

- **Recommendation quality:** run documented MovieLens comparisons, introduce a separate validation split before tuning, and examine coverage alongside ranking accuracy.
- **Vision evaluation:** test on unseen signers, backgrounds, and lighting; inspect per-class errors rather than relying on a single accuracy number.
- **Useful interfaces:** connect models to small applications while documenting hardware, data, and deployment constraints.
- **Software fundamentals:** keep strengthening data structures, algorithms, object-oriented design, APIs, and tests.

I also maintain an [ML project README template](templates/ml-project-readme.md) covering data provenance, reproducible setup, evaluation, and limitations.

## Let's connect

I'm interested in learning-focused collaboration around **recommendation systems, computer vision, and reproducible Python projects**. Helpful feedback on evaluation design, test coverage, and documentation is especially welcome.

- **Discuss a project:** open an issue in the relevant repository with the problem, context, and a reproducible example where possible.
- **Connect professionally:** [LinkedIn](https://www.linkedin.com/in/omkar-solat-os17).
- **Reach out directly:** [omkarsolat2007@gmail.com](mailto:omkarsolat2007@gmail.com).

*These repositories document my learning and engineering practice. Project-specific setup, validation evidence, and limitations live in each repository's README.*
