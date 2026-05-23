<div align="center">

# NLP-Powered Task Intelligence System
### Operational Productivity · Natural Language Processing · ML Deployment

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![spaCy](https://img.shields.io/badge/spaCy_NLP-09A3D5?style=flat-square)](https://spacy.io/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)]()

**Domain:** ML Engineering · NLP · Operational Workflow Automation
**Stack:** Python, Flask, spaCy, scikit-learn, Jupyter
**Deployment:** Local Flask web application

</div>

---

## Executive Summary

This project builds a machine learning system that processes unstructured natural language task descriptions and automatically classifies, prioritizes, and organizes them into actionable workflow items. Rather than requiring structured input, the system interprets free-text descriptions — the way people actually communicate work — and surfaces priority actions through a web interface.

The underlying architecture demonstrates a production-capable NLP pipeline applicable to enterprise task routing, customer service triage, and operational workflow automation.

---

## Challenge

Operational teams generate task backlogs in unstructured formats — emails, messages, verbal notes — that require manual interpretation before they can be acted on. This creates a bottleneck: someone must read, classify, and prioritize each item before the right person can act on it.

The technical challenge was building an NLP system that could reliably extract intent and urgency from varied, informal text inputs and map them to structured task categories — without requiring the user to conform to rigid input schemas.

---

## Action

**NLP Pipeline: spaCy**
spaCy's en_core_web_sm model was used for tokenization, part-of-speech tagging, and named entity recognition. Text preprocessing included lemmatization and stop-word filtering to normalize input variability before feature extraction.

**Classification Model**
A scikit-learn classifier was trained on labeled task examples to predict task category and priority tier. The model was evaluated on held-out data with attention to precision across minority categories — ensuring the system did not default to the most common class.

**Flask Web Application**
The trained model and NLP pipeline were deployed via a Flask application, creating a browser-accessible interface where users submit free-text task descriptions and receive structured, prioritized output in real time.

**Jupyter Notebook: Experimental Pipeline**
The full model development process — data exploration, feature engineering, model selection, and evaluation — is documented in final.ipynb for reproducibility and extension.

---

## Result

| Capability | Detail |
|---|---|
| Input format | Unstructured natural language (free text) |
| Output | Classified task category + priority score |
| Deployment | Flask web app (localhost:5000) |
| NLP model | spaCy en_core_web_sm |
| ML framework | scikit-learn |
| Extensibility | Modular pipeline — replaceable classifier, expandable categories |

The system demonstrates a complete ML engineering cycle: from raw text input through NLP preprocessing, model inference, and web-based output delivery. The architecture is directly extensible to enterprise applications including service desk triage, email routing, and operations workflow management.

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/Balasurya-Ch/Task-Management-System-ML.git
cd Task-Management-System-ML

# 2. Create and activate a virtual environment
python3 -m venv venv
source venv/bin/activate

# 3. Install dependencies
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt

# 4. Download spaCy language model
python -m spacy download en_core_web_sm

# 5. Launch the web application
python app.py
# Navigate to http://localhost:5000
```

For model exploration: Open final.ipynb in Jupyter Lab or VS Code.

---

## Technical Architecture

```
User Input (Free Text via Web Form)
        |
        v
spaCy NLP Pipeline (Tokenization -- Lemmatization -- Entity Recognition)
        |
        v
Feature Extraction
        |
        v
scikit-learn Classifier -- Task Category + Priority Label
        |
        v
Flask Response -- Structured Task Output in Browser
```

**Folder structure:**
```
Task-Management-System-ML/
├── app.py
├── final.ipynb
├── requirements.txt
├── static/
├── templates/
└── README.md
```

---

## Key Insights

NLP-based task classification is most valuable not when replacing human judgment but when handling the high-volume, low-complexity triage that consumes disproportionate analyst time. Automating the first-pass classification of incoming work items — routing them to the right queue before a human reviews — can meaningfully reduce backlog handling time in operational environments.

The spaCy pipeline's modularity means the underlying NLP stage can be upgraded to a larger transformer model for improved accuracy on more complex or domain-specific task language without restructuring the application.

---

<div align="center">
<sub>Balasurya Chandana · Business & Data Analyst · linkedin.com/in/balasurya-chandana</sub>
</div>
