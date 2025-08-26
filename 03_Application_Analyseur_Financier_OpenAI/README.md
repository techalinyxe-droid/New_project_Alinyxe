# Analyseur de Documents Financiers - OpenAI

Application Streamlit moderne pour analyser automatiquement des documents financiers PDF avec OpenAI GPT-4o, offrant la plus haute précision d'analyse.

## Objectif

Transformer rapidement un **rapport financier** (annuel, trimestriel, comptes, bilan, annexes) en un **résumé clair et chiffré** grâce à l'IA générative d'OpenAI.

## Fonctionnalités Implémentées

### Analyse Automatique de PDF
- **Lecture intelligente** : Extraction du texte page par page avec repères clairs
- **Nettoyage automatique** : Suppression des espaces inutiles et formatage
- **Gestion de la longueur** : Limitation automatique pour éviter les dépassements d'API

### IA Générative Spécialisée
- **Modèle OpenAI** : Utilisation de GPT-4o pour l'analyse la plus précise
- **Prompting spécialisé** : Instructions d'analyste financier avec format de sortie structuré
- **Résumé structuré** : Format Markdown avec sections prédéfinies

### Résumé Financier Structuré
Le système génère automatiquement :
- **Informations générales** : Société, période, devise
- **Résumé exécutif** : 5-8 lignes d'analyse
- **Chiffres clés** : Tableau avec indicateurs, valeurs, évolutions et références de pages
- **Analyse détaillée** : Performance, structure financière, risques, outlook
- **Références internes** : Pages et sections à relire

### Questions Interactives
- **Interface de questions** : Possibilité de poser des questions spécifiques sur le PDF
- **Réponses sourcées** : Références aux pages d'origine
- **Précision garantie** : Pas d'invention de données

### Interface Web Streamlit
- **Application web moderne** : Interface intuitive et responsive
- **Upload de fichiers** : Glisser-déposer de PDF directement dans le navigateur
- **Analyse en temps réel** : Résumé et questions sans quitter l'interface
- **Téléchargement** : Export des résumés en format Markdown
- **Questions suggérées** : Interface cliquable pour les questions courantes

## Installation

### 1. Prérequis
- Python 3.10+
- Clé API OpenAI valide
- Document PDF financier à analyser

### 2. Création de l'Environnement Virtuel

#### Méthode 1 : venv (Recommandée)
```bash
# Créer l'environnement virtuel
python -m venv openai_env

# Activer l'environnement
# Sur macOS/Linux :
source openai_env/bin/activate
# Sur Windows :
openai_env\Scripts\activate

# Vérifier l'activation
which python  # macOS/Linux
where python  # Windows
```

#### Méthode 2 : Conda
```bash
# Créer l'environnement conda
conda create -n openai_env python=3.11

# Activer l'environnement
conda activate openai_env

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

### 3. Cloner le repository
```bash
git clone https://github.com/natachanj/GENAIExpress.git
cd GENAIExpress/03_Application_Analyseur_Financier_OpenAI
```

### 4. Installer les dépendances
```bash
# S'assurer que l'environnement virtuel est activé
# L'invite de commande doit commencer par (openai_env)

pip install -r requirements.txt

# Vérifier l'installation
pip list
```

### 5. Installer ipykernel pour Jupyter (optionnel)
```bash
# Si vous voulez utiliser le notebook Jupyter
python -m ipykernel install --user --name openai_env --display-name "OpenAI Analyseur Financier"
```

### 6. Configuration des variables d'environnement
Créer un fichier `.env` à la racine du projet :
```bash
# Copier le fichier d'exemple si disponible
cp env_example.txt .env

# Éditer le fichier .env et ajouter votre clé API
OPENAI_API_KEY=votre_cle_api_openai
```

**Note :** Obtenez votre clé API sur [platform.openai.com](https://platform.openai.com/api-keys)

### 7. Vérifier l'installation
```bash
# Tester Python
python --version

# Tester Streamlit
streamlit --version

# Tester les variables d'environnement
python -c "import os; print('API Key:', os.getenv('OPENAI_API_KEY')[:10] + '...' if os.getenv('OPENAI_API_KEY') else 'Non trouvée')"
```

## Utilisation

### Option 1 : Application Streamlit (Recommandée)

#### Lancer l'Application Streamlit
```bash
# S'assurer que l'environnement virtuel est activé
source openai_env/bin/activate  # macOS/Linux
# ou
conda activate openai_env        # Conda

streamlit run app.py
```

L'application s'ouvrira dans votre navigateur à l'adresse : `http://localhost:8501`

#### Utilisation de l'interface web
1. **Télécharger un PDF** : Glissez-déposez votre document financier
2. **Générer le résumé** : Cliquez sur "Générer le Résumé Financier"
3. **Consulter l'analyse** : Résumé structuré avec chiffres clés
4. **Poser des questions** : Interface de chat pour des questions spécifiques
5. **Exporter** : Télécharger le résumé en Markdown

### Option 2 : Notebook Jupyter

#### Lancer Jupyter Lab
```bash
# Activer l'environnement
source openai_env/bin/activate  # macOS/Linux
# ou
conda activate openai_env        # Conda

jupyter lab
```

#### Utilisation du notebook
1. **Ouvrir le notebook** : Ouvrir `resume_documents_financiers.ipynb`
2. **Sélectionner le kernel** : Dans Jupyter, en haut à droite, sélectionner le kernel "OpenAI Analyseur Financier"
3. **Placer votre PDF** : Mettre votre document financier dans le dossier `data/`
4. **Exécuter les cellules** : Suivre l'ordre des cellules pour l'analyse complète

## Structure du Projet

```
03_Application_Analyseur_Financier_OpenAI/
├── data/
│   └── teslafinancialreport.pdf    # Exemple de document
├── resume_documents_financiers.ipynb  # Notebook principal
├── app.py                          # Application Streamlit
├── requirements.txt                 # Dépendances Python
├── .env                            # Configuration API (à créer)
├── .streamlit/                     # Configuration Streamlit
│   └── config.toml
└── README.md                       # Ce fichier
```

## Technologies Utilisées

- **OpenAI API** : Modèles GPT-4o pour l'analyse de texte la plus précise
- **PyMuPDF** : Lecture et extraction de contenu PDF
- **Python-dotenv** : Gestion des variables d'environnement
- **IPython** : Affichage Markdown dans Jupyter
- **Jupyter** : Environnement de développement interactif
- **Streamlit** : Interface web moderne et responsive

## Format de Sortie

Le résumé généré suit cette structure :

```markdown
# Synthèse financière de [Société] - [Période]

- **Société / Période / Devise** : [Informations]

- **Résumé exécutif** : [5-8 lignes d'analyse]

- **Chiffres clés** :
| Indicateur | Valeur | Évolution/Contexte | Période | Page |
|------------|--------|-------------------|---------|------|
| [Données extraites] |

- **Analyse** : [Performance, Structure, Risques, Outlook]

- **Références internes** : [Pages à relire]
```

## Workflow de Développement

### 1. Première utilisation
```bash
# Cloner le projet
git clone <votre-repo>
cd 03_Application_Analyseur_Financier_OpenAI

# Créer l'environnement virtuel
python -m venv openai_env
source openai_env/bin/activate  # macOS/Linux

# Installer les dépendances
pip install -r requirements.txt

# Configurer l'API OpenAI
# (voir section configuration ci-dessus)

# Lancer l'application
streamlit run app.py
```

### 2. Utilisation quotidienne
```bash
# Activer l'environnement
source openai_env/bin/activate

# Lancer l'application
streamlit run app.py
```

### 3. Mise à jour des dépendances
```bash
# Activer l'environnement
source openai_env/bin/activate

# Mettre à jour
pip install --upgrade -r requirements.txt
```

## Bonnes Pratiques

- **Vérification** : Toujours vérifier les chiffres affichés et leurs pages d'origine
- **Précision** : En cas d'ambiguïté, utiliser "non précisé" plutôt que d'inventer
- **Sécurité** : Limiter la taille des documents pour éviter les dépassements d'API
- **Confidentialité** : Ne pas partager de documents sensibles via l'API
- **Surveillance des coûts** : Surveiller votre consommation d'API OpenAI

## Cas d'Usage

- **Analystes financiers** : Résumé rapide de rapports trimestriels
- **Investisseurs** : Analyse comparative de documents financiers
- **Étudiants** : Compréhension de rapports financiers complexes
- **Consultants** : Préparation de présentations client
- **Auditeurs** : Vérification rapide de documents financiers

## Coûts et Quotas

### Modèles OpenAI et coûts (approximatifs)
- **GPT-4o** : ~$0.005/1K tokens (input), ~$0.015/1K tokens (output)
- **GPT-4 Turbo** : ~$0.01/1K tokens (input), ~$0.03/1K tokens (output)
- **GPT-3.5 Turbo** : ~$0.0005/1K tokens (input), ~$0.0015/1K tokens (output)

### Estimation des coûts
- **Document de 50 pages** : ~$1.00 - $3.00 par analyse
- **Questions supplémentaires** : ~$0.20 - $0.60 par question
- **Usage intensif** : Considérez un plan payant OpenAI

## Sécurité et Confidentialité

- **Communication chiffrée** : Toutes les communications avec OpenAI sont chiffrées
- **Pas de stockage permanent** : Les documents sont traités en mémoire et supprimés
- **Variables d'environnement** : Vos clés API restent locales
- **Audit trail** : Possibilité de tracer l'utilisation de l'API

## Résolution de problèmes

### Erreur de clé API
```bash
# Vérifier que votre fichier .env contient OPENAI_API_KEY=votre_cle
# Assurez-vous que la clé est valide et a des crédits

# Tester la clé
python -c "import os; print('API Key:', os.getenv('OPENAI_API_KEY')[:10] + '...' if os.getenv('OPENAI_API_KEY') else 'Non trouvée')"
```

### Erreur de lecture PDF
- Vérifiez que le PDF n'est pas protégé par mot de passe
- Assurez-vous que le PDF contient du texte (pas uniquement des images)
- Essayez avec un PDF plus simple pour tester

### Réponses imprécises
- Augmentez la longueur maximale du texte dans les paramètres
- Utilisez un modèle plus avancé (GPT-4o)
- Posez des questions plus spécifiques

### Problèmes d'environnement virtuel
```bash
# Si l'environnement ne s'active pas
deactivate  # Désactiver tout environnement actif
source openai_env/bin/activate  # Réactiver

# Si les packages ne sont pas trouvés
pip install --upgrade pip
pip install -r requirements.txt

# Vérifier le chemin Python
which python
pip show streamlit
```

## Évolutions Futures

- [ ] Support multi-format (Word, Excel, PowerPoint)
- [ ] Analyse comparative entre documents
- [ ] Génération automatique de graphiques
- [ ] Export en différents formats (PDF, PowerPoint)
- [ ] Interface web simplifiée
- [ ] Intégration avec des bases de données financières
- [ ] Support multi-langues

## Ressources

- [Documentation OpenAI](https://platform.openai.com/docs)
- [PyMuPDF Documentation](https://pymupdf.readthedocs.io/)
- [Documentation Streamlit](https://docs.streamlit.io/)
- [Challenge GENAIExpress](https://github.com/natachanj/GENAIExpress)

## Liens Utiles

- [OpenAI Platform](https://platform.openai.com/)
- [OpenAI API Keys](https://platform.openai.com/api-keys)
- [OpenAI Pricing](https://openai.com/pricing)
- [Streamlit Documentation](https://docs.streamlit.io/)

**Avantage principal** : Précision maximale avec GPT-4o, analyse la plus avancée disponible !


