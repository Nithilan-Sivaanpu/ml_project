# My ML Project - Pipeline de traduction automatique du français (FR) à l'anglais (EN).

## Description 

Ce Projet a été généré avec Cookiecutter et intègre un pipeline complet de traduction automatique et d'évaluation de la qualité des traductions.

## Structure du projet 

```
ml_project/
├──.github/
│     └── workflows/
│         └── CI.yml  #Pipeline CI/CD GitHub Actions
├──src/
│    ├──loaders/  #Chargement des données (CSV, JSON)
│    ├──processors/  #Prétraitement des données : transformation et nettoyage des donnnées
│    ├──translators/  #Interface avec les modèles de traduction HuggingFace
│    ├──evaluators/  #Calcul des métriques de qualité (BLEU, chrf)
│    ├── orchestrator/  #Coordination du pipeline : module principal qui coordonne toutes les étapes du pipeline
│    ├──config.py  #Configuration centralisée
│    └──main.py  #Point d'entrée principal
├──data/
│    ├── sample.json  #Données d'exemple
│    └──sample02.json  #Données d'exemple 2
├──output/  #Traductions générés par le pipeline
├──tests/
│    └──test_basic.py  #Test unitaires
├──README.md  #Information sur le déroulement du projet
├──pyproject.toml
└──.gitignore
```

## Prérequis 

- Python 3.10+
- pip

## Installation 

### 1. Cloner le dépôt 

Terminal Powershell ou bash

git clone https://github.com/Nithilan-Sivaanpu/ml_project.git
cd ml_project

### 2. Créer et activer l'environnement virtuel 

python -m venv .venv

#Windows
.venv\Scripts\Activate.ps1

#Linux / macOS
source .venv/bin/activate

### 3. Installer les dépendances  

pip install -r requirement.txt

### 4. Lancer le pipeline  

python src/main.py

### Résultat attendu  

Loaded 20 rows.
Traduction: 100%|██████████| 15/15
Saved translated file to: output/translated.csv
Translation quality metrics:
BLEU: 41.61
chrF: 70.46

## Tests à effectuer 

pytest

Pytest est un outil qui permet de vérifier automatiquement que le code fonctionne correctement. Il détecte et exécute tous les fichiers commençant par "test_" dans le répertoire "tests/".

Dans ce projet, pytest permet de :
- Vérifier que la structure du projet est correctement initialisée
- S'assurer qu'aucune modification du code ne casse le fonctionnement existant
- Reproduire les mêmes vérifications que le pipeline CI/CD GitHub Actions

Résultat attendu :

1 passed in 0.01s

## Formatage du code 

"Black" est un outil de formatage automatique du code Python. Il garantit que tout le code respecte un style uniforme et lisible, sans avoir à se soucier manuellement de l'indentation, des espaces ou des sauts de ligne, afin de produire un code professionnel et conforme aux standards Python

#Vérifier :

black --check .

Résultat attendu :

All done! ✨ 🍰 ✨
13 files would be left unchanged.

#Appliquer

black .

## CI/CD

Le projet intègre un pipeline GitHub Actions qui s'exécute automatiquement à chaque push sur main :
- Installation des dépendances
- Exécution des tests pytest
- Vérification du formatage black

## Auteur 

Sivaanpu Nithilan

## Modèle utilisé 

- **Helsinki-NLP/opus-mt-fr-en** — Modèle de traduction français → anglais basé sur l'architecture Marian NMT

