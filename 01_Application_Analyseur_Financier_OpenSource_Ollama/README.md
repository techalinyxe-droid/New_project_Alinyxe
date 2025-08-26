# Analyseur de Documents Financiers - Ollama

Application Streamlit moderne pour analyser des documents financiers PDF en utilisant Ollama avec le modèle Llama 3.1.

## Fonctionnalités

- **Import PDF** : Interface drag & drop pour vos documents financiers
- **Analyse Automatique** : Extraction de texte et génération de résumés structurés
- **Questions Interactives** : Chat pour poser des questions spécifiques
- **Interface Moderne** : Design élégant et responsive
- **Export** : Téléchargement des résumés en Markdown

## Installation

### 1. Prérequis

- Python 3.8+
- Ollama installé et configuré

### 2. Création de l'Environnement Virtuel

#### Méthode 1 : venv (Recommandée)
```bash
# Créer l'environnement virtuel
python -m venv ollama_env

# Activer l'environnement
# Sur macOS/Linux :
source ollama_env/bin/activate
# Sur Windows :
ollama_env\Scripts\activate

# Vérifier l'activation
which python  # macOS/Linux
where python  # Windows
```

#### Méthode 2 : Conda
```bash
# Créer l'environnement conda
conda create -n ollama_env python=3.11

# Activer l'environnement
conda activate ollama_env

# Vérifier l'activation
conda info --envs
```

#### Méthode 3 : Poetry
```bash
# Installer Poetry si pas déjà fait
curl -sSL https://install.python-poetry.org | python3 -

# Créer et activer l'environnement
poetry install
poetry shell
```

### 3. Installer Ollama

```bash
# macOS
brew install ollama

# Linux
curl -fsSL https://ollama.ai/install.sh | sh

# Windows
# Télécharger depuis https://ollama.ai
```

### 4. Démarrer Ollama et télécharger le modèle

```bash
# Démarrer le service
ollama serve

# Dans un autre terminal, télécharger Llama 3.1
ollama pull llama3.1:8b
```

### 5. Installer les dépendances Python

```bash
# S'assurer que l'environnement virtuel est activé
# L'invite de commande doit commencer par (ollama_env) ou (ollama_env)

# Installer les dépendances
pip install -r requirements.txt

# Vérifier l'installation
pip list
```

### 6. Vérifier l'installation

```bash
# Tester Python
python --version

# Tester Streamlit
streamlit --version

# Tester Ollama
ollama list
```

## Utilisation

### 1. Lancer l'application

```bash
# S'assurer que l'environnement virtuel est activé
source ollama_env/bin/activate  # macOS/Linux
# ou
conda activate ollama_env        # Conda

# Lancer l'application
streamlit run app.py
```

### 2. Configurer Ollama

- L'application vérifie automatiquement la connexion à Ollama
- Sélectionnez le modèle souhaité dans la sidebar (llama3.1:8b, llama3.1:70b, ou llama3.1:latest)
- Ajustez les paramètres de température et de longueur selon vos besoins

### 3. Analyser un document

1. **Importer un PDF** : Glissez-déposez votre document financier
2. **Cliquer sur "Analyser"** : L'application extrait le texte et génère un résumé
3. **Consulter le résumé** : Analyse structurée avec chiffres clés et références de pages
4. **Poser des questions** : Interface de chat pour des questions spécifiques

## Format des Résumés

Les résumés générés incluent :

- **Société / Période / Devise** : Informations d'identification
- **Résumé exécutif** : Synthèse des faits marquants
- **Chiffres clés** : Tableau des indicateurs avec références de pages
- **Analyse** : Performance, structure financière, risques, outlook
- **Références internes** : Pages et sections importantes

## Configuration

### Paramètres d'analyse

- **Longueur maximale du texte** : Limite le nombre de caractères traités (50k-200k)
- **Longueur du résumé** : Nombre de mots cible pour le résumé (150-500)
- **Température** : Contrôle la créativité des réponses (0.0-1.0)

### Modèles disponibles

- `llama3.1:8b` : Modèle rapide, bon compromis performance/qualité
- `llama3.1:70b` : Modèle plus précis, plus lent
- `llama3.1:latest` : Dernière version disponible

## Dépannage

### Erreur de connexion Ollama

```bash
# Vérifier que le service est démarré
ollama serve

# Vérifier les modèles disponibles
ollama list

# Redémarrer le service si nécessaire
pkill ollama
ollama serve
```

### Modèle non trouvé

```bash
# Télécharger le modèle
ollama pull llama3.1:8b

# Vérifier l'installation
ollama list
```

### Performance lente

- Utilisez `llama3.1:8b` au lieu de `llama3.1:70b`
- Réduisez la longueur maximale du texte
- Ajustez la température à 0.1 pour des réponses plus rapides

### Problèmes d'environnement virtuel

```bash
# Si l'environnement ne s'active pas
deactivate  # Désactiver tout environnement actif
source ollama_env/bin/activate  # Réactiver

# Si les packages ne sont pas trouvés
pip install --upgrade pip
pip install -r requirements.txt

# Vérifier le chemin Python
which python
pip show streamlit
```

## Structure du Projet

```
01_Application_Analyseur_Financier_OpenSource_Ollama/
├── app.py                          # Application principale
├── requirements.txt                # Dépendances Python
├── .streamlit/
│   └── config.toml               # Configuration Streamlit
├── data/                          # Dossier pour vos PDF
│   └── teslafinancialreport.pdf  # Document d'exemple
└── README.md                      # Ce fichier
```

## Personnalisation

### Modifier le style CSS

Éditez la section CSS dans `app.py` pour personnaliser l'apparence :

```python
st.markdown("""
<style>
    .main-header {
        background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
        /* Personnalisez les couleurs ici */
    }
</style>
""", unsafe_allow_html=True)
```

### Ajouter de nouveaux modèles

Modifiez la liste des modèles dans la sidebar :

```python
model = st.selectbox(
    "Modèle Ollama",
    ["llama3.1:8b", "llama3.1:70b", "llama3.1:latest", "votre-modele"],
    index=0
)
```

## Exemples d'Utilisation

### Questions typiques

- "Quel est le chiffre d'affaires ?"
- "Quelle est la marge nette ?"
- "Quels sont les principaux risques identifiés ?"
- "Quelle est la dette nette ?"
- "Quel est l'outlook pour l'année prochaine ?"

### Types de documents supportés

- Rapports annuels
- Rapports trimestriels
- Comptes de résultats
- Bilans
- Annexes financières

## Workflow de Développement

### 1. Première utilisation
```bash
# Cloner le projet
git clone <votre-repo>
cd 01_Application_Analyseur_Financier_OpenSource_Ollama

# Créer l'environnement virtuel
python -m venv ollama_env
source ollama_env/bin/activate  # macOS/Linux

# Installer les dépendances
pip install -r requirements.txt

# Installer et configurer Ollama
# (voir section installation ci-dessus)

# Lancer l'application
streamlit run app.py
```

### 2. Utilisation quotidienne
```bash
# Activer l'environnement
source ollama_env/bin/activate

# Lancer l'application
streamlit run app.py
```

### 3. Mise à jour des dépendances
```bash
# Activer l'environnement
source ollama_env/bin/activate

# Mettre à jour
pip install --upgrade -r requirements.txt
```

## Contribution

Pour contribuer au projet :

1. Fork le repository
2. Créez une branche pour votre fonctionnalité
3. Committez vos changements
4. Poussez vers la branche
5. Ouvrez une Pull Request

## Licence

Ce projet est sous licence MIT. Voir le fichier LICENSE pour plus de détails.

## Support

Si vous rencontrez des problèmes :

1. Vérifiez que Ollama est correctement installé et démarré
2. Consultez la section dépannage ci-dessus
3. Vérifiez que votre environnement virtuel est activé
4. Ouvrez une issue sur GitHub avec les détails de l'erreur

## Liens Utiles

- [Documentation Ollama](https://ollama.ai/docs)
- [Documentation Streamlit](https://docs.streamlit.io/)
- [Modèles Llama disponibles](https://ollama.ai/library)
- [Guide d'installation Ollama](https://ollama.ai/download)

---

**Développé pour l'analyse automatisée de rapports financiers**

**Avantage principal** : Traitement 100% local, aucune donnée externe, confidentialité maximale !
