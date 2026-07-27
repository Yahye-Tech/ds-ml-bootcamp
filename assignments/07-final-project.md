# Assignment 7 – Final Project

**Goal:** Build a complete ML project of your own choice — from dataset preparation, through training and comparing **at least three algorithms**, to deploying the **best model** as an API. This is your capstone: you choose the problem, dataset, and approach.

---

## Overview

This assignment tests your ability to:

- Define a real ML problem
- Collect and process data
- Train and compare **at least three different algorithms**
- Select the **best overall model** with clear justification
- Deploy a working API
- Document your work professionally

---

## Requirements

### 1. GitHub Repository

Build the full project in a **GitHub repository on your own account**.

- Create the repo under **your** username (not a zip file, not Google Drive, not a fork of the bootcamp repo).
- Ensure your instructor can access it (public, or private with instructor invited).
- Organize code into logical folders, for example: `dataset/`, `src/`, `api/`, `models/`.
- Use meaningful commit messages throughout development.

Example layout:

```
project-repo/
├── dataset/
├── src/
│   ├── preprocess.py
│   └── train.py
├── api/
│   └── app.py
├── models/
├── README.md
└── project_paper.md
```

---

### 2. Dataset

- Use a dataset with at least **1,000 samples**.
- Document the source (Kaggle, UCI, OpenML, self-collected, etc.) with a **link** in your README.
- Implement preprocessing in code (cleaning, imputation, encoding, scaling, etc.) — not only described in the paper.

Pick a dataset that fits a clear ML problem:

- **Classification** — predict a category (e.g. loan approved yes/no)
- **Regression** — predict a number (e.g. house price, sales amount)
- **Clustering** — discover groups without labels (e.g. customer segments)

> Supervised projects (regression or classification) are the easiest to deploy with a `/predict` API. If you choose clustering, explain how your API assigns new rows to a segment.

**Where to find datasets:**

| Source | Link |
| --- | --- |
| Kaggle | [kaggle.com/datasets](https://www.kaggle.com/datasets) |
| UCI ML Repository | [archive.ics.uci.edu/ml](https://archive.ics.uci.edu/ml) |
| OpenML | [openml.org](https://www.openml.org/) |
| Google Dataset Search | [datasetsearch.research.google.com](https://datasetsearch.research.google.com/) |

Do **not** reuse the bootcamp classroom datasets as-is (housing, loan approval, wholesale customers). Choose your own problem.

---

### 3. Algorithms (At Least Three)

Train **at least three different algorithms** on the same prepared data. You may train more — three is the minimum.

- All algorithms must be **distinct**.
- At least **two** should come from the bootcamp (e.g. Linear/Logistic Regression, Decision Tree, Random Forest, K-Means).
- Additional algorithms may be ones you researched independently (e.g. SVM, Gradient Boosting, XGBoost, DBSCAN, GMM).
- Use the **same train/test split** (or the same cross-validation strategy) for every model so the comparison is fair.

Print a **comparison table** with one row per algorithm:

| Algorithm | Metric 1 | Metric 2 | Metric 3 | ... |
| --- | --- | --- | --- | --- |
| Model A | ... | ... | ... | ... |
| Model B | ... | ... | ... | ... |

**Select the best overall model** using a clear rule (e.g. highest F1, lowest MAE, highest Silhouette). State the rule in your README and paper, and explain **why** that metric fits your problem.

- Save and deploy **only the best model** (+ scaler, encoders, or other artifacts needed at inference time).

---

### 4. Model Evaluation

- Show evaluation results for **every model you trained** in the comparison table.
- Run at least **3 sanity checks** on the **best model** — sample inputs with predictions (show input features and model output).
- Use metrics that match your problem type:
  - **Classification:** Accuracy, Precision, Recall, F1, Confusion Matrix
  - **Regression:** MAE, RMSE, R²
  - **Clustering:** Silhouette Score, Davies–Bouldin Index, cluster interpretation

---

### 5. Deployment

- Expose your **best trained model** as an API using **Flask** or **FastAPI**.
- Endpoint **`/predict`** must accept **JSON input** and return **JSON predictions**.
- The API must run locally and respond correctly when tested.

**Optional (extra credit):** Add a simple frontend (HTML form or Streamlit) that calls your API.

Example `curl` test (adjust fields to your project):

```bash
curl -X POST http://127.0.0.1:8000/predict \
  -H "Content-Type: application/json" \
  -d '{"feature1": 100, "feature2": "Urban", "feature3": 1}'
```

---

### 6. README.md

Your repo must include a `README.md` with:

- Project title and description
- Your **certificate name** (full name as it should appear on the Goobo Labs certificate)
- Dataset details (source, size, link)
- All **algorithms** used (minimum of three)
- Comparison table summary and **which model won**
- Example commands to train and run the API
- Example API usage with `curl`
- Results summary (2–3 sentences)

---

### 7. Project Paper

Include `project_paper.md` or `project_paper.pdf` in your repo.

**Length:** 3–5 pages.

**Required sections:**

1. **Problem statement and motivation** — What problem did you solve? Why does it matter?
2. **Dataset and preprocessing** — Source, size, features, cleaning steps.
3. **Algorithms** — Every model you trained (at least three): how each works and why you chose it.
4. **Results and discussion** — Comparison table, sanity checks, which model performed best and why.
5. **Deployment notes** — How the API works; example request and response; frontend if included.
6. **Lessons learned** — Challenges faced, what you would improve, key takeaways.

---

## Expected Deliverables

A working GitHub repository containing:

- Training and inference code
- All trained models compared (minimum of three)
- Best model saved and deployed via API
- `README.md` with setup, results, and certificate name
- `project_paper.md` or `project_paper.pdf`

The API must run locally and respond correctly to `/predict`.

---

## Evaluation Criteria

| Criterion | What we look for |
| --- | --- |
| Problem choice and definition | Clear, realistic, well-motivated |
| Data cleaning and preprocessing | Reproducible pipeline in code |
| At least three algorithms trained and compared | Same split, fair comparison |
| Best model selection | Justified with metrics; winner deployed |
| Model evaluation and sanity checks | Metrics + at least 3 sample predictions on best model |
| Working API deployment | `/predict` accepts JSON, returns JSON, runs locally |
| Documentation | README + 3–5 page paper |
| Code quality and commit history | Organized repo, logical commits |

---

## Tips

- Train all your models in one script or notebook section so the comparison table is easy to reproduce.
- Test your API with `curl` or Postman before submitting — a broken `/predict` endpoint is the most common failure.
- Supervised projects (regression/classification) are the most straightforward for API deployment. If you chose clustering, make sure `/predict` returns a meaningful segment label for new input rows.

---

## Resources

| Topic | Link |
| --- | --- |
| Flask | [flask.palletsprojects.com](https://flask.palletsprojects.com/) |
| FastAPI | [fastapi.tiangolo.com](https://fastapi.tiangolo.com/) |
| scikit-learn | [scikit-learn.org/stable/documentation.html](https://scikit-learn.org/stable/documentation.html) |
| Saving models | [scikit-learn model persistence](https://scikit-learn.org/stable/model_persistence.html) |
| Classroom deployment demo | [`../deployment/`](../deployment/) |

---

*End of Assignment 7*
