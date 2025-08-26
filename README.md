# GENAI - Maîtrise de l'IA Générative

## Vue d'ensemble

Ce projet contient **3 applications d'analyseur financier** utilisant différentes technologies d'IA générative pour analyser automatiquement des documents financiers PDF et générer des résumés structurés.

## Objectif

Transformer rapidement des **rapports financiers** (annuels, trimestriels, comptes, bilans, annexes) en **résumés clairs et chiffrés** grâce à l'IA générative, avec une interface moderne et intuitive.

## Architecture du Projet

```
GENAI/
├── 01_Application_Analyseur_Financier_OpenSource_Ollama/
│   ├── Ollama + Llama 3.1 (Open Source)
│   ├── Interface Streamlit moderne
│   └── Traitement local, pas de données externes
│
├── 02_Application_Analyseur_Financier_OpenSource_OpenRouter/
│   ├── OpenRouter (accès à multiples modèles)
│   ├── Interface Streamlit élégante
│   └── Performance optimisée
│
└── 03_Application_Analyseur_Financier_OpenAI/
    ├── OpenAI GPT-4o (plus avancé)
    ├── Interface Streamlit 
    └── Analyse la plus précise
```

## Fonctionnalités Principales

### Import et Analyse PDF
- **Upload drag & drop** de documents financiers
- **Extraction intelligente** du texte page par page
- **Nettoyage automatique** et formatage
- **Gestion de la longueur** pour éviter les dépassements

### IA Générative Spécialisée
- **Résumés structurés** au format Markdown
- **Analyse financière** avec chiffres clés
- **Questions interactives** sur le contenu
- **Références de pages** pour vérification

### Interface Moderne
- **Streamlit** pour une expérience web fluide
- **Design responsive** et intuitif
- **Export des résumés** en différents formats
- **Historique des questions** pendant la session

## Démarrage Rapide

### 1. Prérequis Système
```bash
# Vérifier Python
python --version  # Python 3.8+ requis

# Vérifier pip
pip --version
```

### 2. Cloner le Projet
```bash
git clone <votre-repo>
cd GENAI
```

### 3. Choisir une Application

#### **Option 1 : Ollama (Open Source, Local)**
```bash
cd 01_Application_Analyseur_Financier_OpenSource_Ollama
# Suivre le README détaillé du dossier
```

#### **Option 2 : OpenRouter (Multi-modèles)**
```bash
cd 02_Application_Analyseur_Financier_OpenSource_OpenRouter
# Suivre le README détaillé du dossier
```

#### **Option 3 : OpenAI (Plus Avancé)**
```bash
cd 03_Application_Analyseur_Financier_OpenAI
# Suivre le README détaillé du dossier
```

## Création d'Environnement Virtuel

### Méthode 1 : venv (Recommandée)
```bash
# Créer l'environnement
python -m venv genai_env

# Activer l'environnement
# Sur macOS/Linux :
source genai_env/bin/activate
# Sur Windows :
genai_env\Scripts\activate

# Installer les dépendances
pip install -r requirements.txt
```

### Méthode 2 : Conda
```bash
# Créer l'environnement
conda create -n genai_env python=3.11

# Activer l'environnement
conda activate genai_env

# Installer les dépendances
pip install -r requirements.txt
```

### Méthode 3 : Poetry
```bash
# Installer Poetry si pas déjà fait
curl -sSL https://install.python-poetry.org | python3 -

# Créer et activer l'environnement
poetry install
poetry shell
```

## Comparaison des Solutions

| Critère | Ollama | OpenRouter | OpenAI |
|---------|--------|------------|---------|
| **Coût** | Gratuit | Pay-per-use | Pay-per-use |
| **Confidentialité** | 100% Local | API externe | API externe |
| **Performance** | Rapide | Très rapide | Très précise |
| **Modèles** | Llama 3.1 | Multi-modèles | GPT-4o |
| **Installation** | Simple | API Key | API Key |
| **Utilisation** | Hors ligne | En ligne | En ligne |

## Cas d'Usage Recommandés

### **Ollama** - Pour :
- **Confidentialité maximale** (données sensibles)
- **Utilisation hors ligne**
- **Coût zéro**
- **Tests et développement**

### **OpenRouter** - Pour :
- **Performance optimale**
- **Accès à multiples modèles**
- **Coût contrôlé**
- **Production légère**

### **OpenAI** - Pour :
- **Précision maximale**
- **Analyse complexe**
- **Production professionnelle**
- **Budget disponible**

## Structure des Données

Chaque application inclut :
```
data/
└── teslafinancialreport.pdf    # Document d'exemple
```

## Sécurité et Confidentialité

- **Ollama** : Traitement 100% local, aucune donnée externe
- **OpenRouter/OpenAI** : Communication chiffrée, pas de stockage permanent
- **Tous** : Suppression automatique des fichiers après traitement

## Développement

### Ajouter une Nouvelle Application
1. Créer un nouveau dossier avec le préfixe numérique
2. Copier la structure de base d'une application existante
3. Adapter le code pour la nouvelle technologie
4. Mettre à jour ce README principal

### Tests
```bash
# Lancer l'application
streamlit run app.py

# Vérifier dans le navigateur
# http://localhost:8501
```

## Documentation

- **README principal** : Ce fichier (vue d'ensemble)
- **README spécifiques** : Dans chaque dossier d'application
- **Code source** : Commentaires détaillés dans les fichiers Python

## Contribution

1. **Fork** le repository
2. **Créer** une branche pour votre fonctionnalité
3. **Commiter** vos changements
4. **Pousser** vers la branche
5. **Ouvrir** une Pull Request

## Licence

Ce projet est sous licence MIT. Voir le fichier LICENSE pour plus de détails.

## Support et Dépannage

### Problèmes Communs
1. **Erreur de dépendances** : Vérifier la version de Python et recréer l'environnement virtuel
2. **Erreur d'API** : Vérifier les clés API et les quotas
3. **Erreur Ollama** : Vérifier que le service est démarré et les modèles téléchargés

### Ressources
- [Documentation Streamlit](https://docs.streamlit.io/)
- [Documentation OpenAI](https://platform.openai.com/docs)
- [Documentation Ollama](https://ollama.ai/docs)
- [Documentation OpenRouter](https://openrouter.ai/docs)

---

## Prêt à Démarrer ?

Choisissez votre solution préférée et suivez le README détaillé du dossier correspondant !

**Conseil** : Commencez par **Ollama** pour tester gratuitement, puis passez aux solutions cloud selon vos besoins.

---

**Développé pour maîtriser l'IA générative**
