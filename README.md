# ANIP Facial OCR Challenge

Ce projet contient les solutions pour le challenge ANIP comprenant trois tâches principales :

## Structure du projet

```
anip-challenge/
├── data/
│   ├── tache1_facial_recognition/
│   │   ├── train/
│   │   └── test/
│   ├── tache2_age_estimation/
│   │   ├── train/
│   │   └── test/
│   └── tache3_ocr_fraud/
│       ├── train/
│       └── test/
│
├── notebooks/
│   ├── 1_facial_recognition.ipynb
│   ├── 2_age_estimation.ipynb
│   └── 3_ocr_fraud_detection.ipynb
│
├── src/
│   ├── utils.py          # Fonctions utiles
│   └── models.py         # Architectures de modèles
│
├── requirements.txt      # Dépendances Python
│
├── README.md             # Ce fichier
│
└── submissions/          # Soumissions
```

## Tâches

### Tâche 1 : Reconnaissance Faciale
- **Objectif :** Identifier et classer les visages
- **Notebook :** `notebooks/1_facial_recognition.ipynb`

### Tâche 2 : Estimation d'Âge
- **Objectif :** Prédire l'âge à partir d'images faciales
- **Notebook :** `notebooks/2_age_estimation.ipynb`

### Tâche 3 : Détection de Fraude OCR
- **Objectif :** Détecter les fraudes dans les documents via OCR
- **Notebook :** `notebooks/3_ocr_fraud_detection.ipynb`

## Installation

```bash
pip install -r requirements.txt
```

## Scores

[À remplir après évaluation]