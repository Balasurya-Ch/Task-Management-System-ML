<div align="center">

# NLP-Powered Task Intelligence System

### Operational Productivity · Natural Language Processing · ML Deployment

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![spaCy](https://img.shields.io/badge/spaCy_NLP-09A3D5?style=flat-square)](https://spacy.io/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)]()

| | |
|---|---|
| **Domain** | ML Engineering · NLP · Operational Workflow Automation |
| **Stack** | Python, Flask, spaCy, scikit-learn, Jupyter |
| **Deployment** | Local Flask web application (localhost:5000) |
| **Use Case** | Automated task classification and priority scoring from free-text input |

</div>

---

## The Business Problem

Operational teams spend a disproportionate amount of time on the lowest-value part of their workflow: reading unstructured inputs (emails, messages, notes), deciding what category each item belongs to, and assigning a priority level before any actual work begins. This first-pass triage is manual, inconsistent, and doesn't scale.

**The question:** Can a machine handle the classification and prioritization of incoming task descriptions reliably enough to route them to the right queue automatically — so that analysts spend time on analysis, not triage?

---

## Challenge

The technical challenge was building a system that accepts completely unstructured natural language — the way people actually communicate work, not the way a form requires them to format it — and extracts structured, actionable output reliably.

Free-text task descriptions are messy: variable length, informal language, missing context, inconsistent terminology across users. A rule-based system would fail on edge cases. A classification model needed enough labeled diversity to generalize, and the NLP preprocessing layer needed to normalize the input sufficiently before the model ever saw it.

Deployment also mattered. A Jupyter notebook that stays on a local machine has no operational value. The system needed to be accessible through a browser interface.

---

## Action

**spaCy NLP Pipeline — Input Normalization**
The `en_core_web_sm` spaCy model handled tokenization, part-of-speech tagging, lemmatization, and named entity recognition. Stop-word filtering and lemmatization normalized the input before feature extraction — reducing vocabulary noise and improving model generalization across different users' phrasing styles.

**scikit-learn Classifier — Task Categorization**
A classification model was trained on labeled task examples to predict both category and priority tier. Model evaluation focused on precision-recall across all classes (not just accuracy), explicitly handling class imbalance in the training set to prevent the model from defaulting to the most common category.

**Flask Web Application — From Model to Interface**
The trained pipeline was wrapped in a Flask application that serves a browser-accessible form at localhost:5000. Users submit free-text descriptions; the application returns structured output in real time. This transforms the model from an experiment into a usable tool.

**Jupyter Notebook — Full Development Record**
`final.ipynb` documents the complete development pipeline: data exploration, preprocessing decisions, model selection rationale, and evaluation metrics. The notebook serves as both a reproducibility record and an extension point for future model improvements.

---

## Result

| Capability | Detail |
|---|---|
| Input | Unstructured free-text task descriptions |
| Output | Classified task category + priority score |
| Deployment | Flask web app (localhost:5000) |
| NLP layer | spaCy en_core_web_sm — tokenization, lemmatization, NER |
| Classification | scikit-learn — precision-recall optimized |
| Cold start | No structured input required from user |
| Extensibility | Modular pipeline — classifier and NLP model are independently swappable |

**Why this matters at scale:** Enterprise service desks, operations centers, and customer support teams handle thousands of unstructured inputs per day. A triage system that automates the first-pass classification doesn't just save time — it standardizes routing logic and creates a data trail that enables backlog analysis, capacity planning, and workflow optimization over time.

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/Balasurya-Ch/Task-Management-System-ML.git
cd Task-Management-System-ML

# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate        # Mac/Linux
venv\Scripts\activate           # Windows

# Install dependencies
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt

# Download spaCy model
python -m spacy download en_core_web_sm

# Launch application
python app.py
# Open browser: http://localhost:5000
```

For model exploration: open `final.ipynb` in Jupyter Lab or VS Code.

---

## Technical Architecture

```
Free-Text Input (Browser Form)
            |
            v
    spaCy NLP Pipeline
    Tokenization | Lemmatization | Stop-word filtering | NER
            |
            v
    Feature Extraction
            |
            v
    scikit-learn Classifier
    Task category | Priority tier
            |
            v
    Flask Response
    Structured output rendered in browser
```

**Repository structure:**
```
Task-Management-System-ML/
├── app.py              Flask application entry point
├── final.ipynb         Model development and evaluation
├── requirements.txt    Dependency manifest
├── static/             CSS and static assets
├── templates/          HTML templates
└── README.md
```

---

## Key Insights

The most important design decision in this system is the separation between the NLP preprocessing layer and the classification layer. They are independently swappable: the spaCy model can be upgraded to a larger transformer (`en_core_web_trf`) for higher accuracy on complex input without touching the classifier. The classifier can be swapped for a different algorithm without rebuilding the NLP pipeline.

This modularity is what makes the system practical for extension. A production deployment would replace the scikit-learn classifier with a model trained on domain-specific task data and add a feedback loop to capture misclassifications — improving accuracy over time with real usage data.

The business analogy: this is architecturally identical to what powers enterprise service-desk ticket classification, customer email routing, and operations workflow systems. The difference is scale, training data, and feedback infrastructure — not the fundamental design.

---

<div align="center">

**[Balasurya Chandana](https://linkedin.com/in/balasurya-chandana)** · Business & Data Analyst · [linkedin.com/in/balasurya-chandana](https://linkedin.com/in/balasurya-chandana)

</div>
