# Arcane

**ARCANE** (Automated Resume and Cover letter ANalysis Engine) est un système intelligent modulaire qui automatise la création de CV personnalisés, lettres de motivation et préparation d'entretiens en utilisant l'IA Claude Sonnet 4.5.

[![Python](https://img.shields.io/badge/Python-3.14+-blue.svg)](https://www.python.org/)
[![Claude](https://img.shields.io/badge/Claude-Sonnet%204.5-purple.svg)](https://www.anthropic.com/)
[![Architecture](https://img.shields.io/badge/Architecture-Modulaire-green.svg)](ARCHITECTURE.md)

---

## ✨ Nouveauté : Architecture Modulaire

ARCANE v2 propose une **architecture à modes multiples** :

```
📂 ARCANE/
├── core/        # 🎯 Cœur du système (un seul code Python)
├── templates/   # 📄 Templates LaTeX (CV, lettre)
└── modes/       # 🎭 6 modes d'utilisation préconfigurés
```

**Avantages :**
- ✅ **Un seul code à maintenir** (`core/`)
- ✅ **6 modes d'utilisation** prêts à l'emploi
- ✅ **Profils multiples** (spécifique/générique)
- ✅ **Configurations indépendantes** par mode

📖 **Voir [ARCHITECTURE.md](ARCHITECTURE.md) pour les détails complets**

---

## 🎭 Les 6 Modes Disponibles

| Mode | Usage | Profil |
|------|-------|--------|
| **🔍 Recherche Complète Générique** | Recherche + génération multi-offres | Générique (tout métier) |
| **🔍 Recherche Complète Spécifique** | Recherche + génération multi-offres | Spécifique (votre profil) |
| **📋 Génération URLs Générique** | Batch depuis liste d'URLs | Générique |
| **📋 Génération URLs Spécifique** | Batch depuis liste d'URLs | Spécifique |
| **📄 Génération Simple Générique** | Une seule offre | Générique |
| **📄 Génération Simple Spécifique** | Une seule offre | Spécifique |

### 🎯 Mode Interactif (Nouveau !)

**Tous les modes sont maintenant 100% interactifs !** Plus besoin de mémoriser les arguments en ligne de commande.

```bash
cd modes/generation_simple_specifique/
./lancer.sh
# ✨ Le script vous guide étape par étape !
```

**Ce qui vous sera demandé selon le mode :**
- 📄 **Génération Simple** : URL de l'annonce
- 📋 **Génération URLs** : Source des URLs (fichier, manuel, personnalisé)
- 🔍 **Recherche Complète** : 8 paramètres (poste, localisation, séniorité, etc.)

📖 **Voir [GUIDE_INTERACTIF.md](documentation/GUIDE_INTERACTIF.md) pour tous les détails**

---

## ✨ Fonctionnalités

### 🎯 **Génération Automatique**
- ✅ **CV personnalisé** (PDF) adapté à chaque offre
- ✅ **Lettre de motivation** (PDF) ciblée
- ✅ **Topo de préparation d'entretien** avec insights stratégiques
- ✅ **10 questions techniques** avec réponses détaillées
- ✅ **5 questions de personnalité** (méthode STAR)

### 🔍 **Recherche Intelligente**
- ✅ **Recherche multi-plateformes** (LinkedIn, Indeed, WTTJ, Apec)
- ✅ **Analyse de pertinence IA** (scoring automatique /10)
- ✅ **Critères avancés** (séniorité, domaines, type d'entreprise)
- ✅ **Scraping WTTJ** avec Playwright (optionnel)

### 📝 **Personnalisation Avancée**
- ✅ **2 templates CV** : Classique 1 colonne ou Moderne 2 colonnes
- ✅ **Styles configurables** : polices, couleurs, puces, marges
- ✅ **Prompts IA personnalisables** pour chaque section
- ✅ **Mode candidature spontanée** (analyse site web entreprise)

### 🎭 **Multi-Profils**
- ✅ **Mode spécifique** : Catégories hardcodées (votre profil)
- ✅ **Mode générique** : Catégories dynamiques (tout profil)
- ✅ **Configurations indépendantes** par mode

---

## 📋 Prérequis

- **Python 3.14+**
- **LaTeX** (MacTeX, MiKTeX ou TeX Live)
- **Clé API Claude** (Anthropic)
- **Playwright** (optionnel, pour scraping WTTJ)

---

## 🚀 Installation

### 1️⃣ **Cloner le Repository**
```bash
git clone https://github.com/Mirouxe/ARCANE.git
cd ARCANE
```

### 2️⃣ **Créer l'Environnement Virtuel**
```bash
python3 -m venv venv
source venv/bin/activate  # macOS/Linux
# ou
venv\Scripts\activate  # Windows
```

### 3️⃣ **Installer les Dépendances**
```bash
pip install -r requirements.txt
```

### 4️⃣ **Installer LaTeX**

**macOS:**
```bash
brew install --cask mactex
```

**Linux:**
```bash
sudo apt-get install texlive-full
```

**Windows:**  
Téléchargez [MiKTeX](https://miktex.org/)

### 5️⃣ **Configurer l'API Claude**

1. Obtenez votre clé API sur [console.anthropic.com](https://console.anthropic.com/)
2. Créez un fichier `.env` :
```bash
echo "ANTHROPIC_API_KEY=sk-ant-votre-cle-api-ici" > .env
```

### 6️⃣ **[Optionnel] Installer Playwright pour WTTJ**

```bash
./documentation/installer_playwright.sh
```

---

## ⚡ Démarrage Rapide

### Pour Votre Usage Personnel (Profil Spécifique) ⭐

```bash
# Génération simple (une offre)
cd modes/generation_simple_specifique/
./lancer.sh https://www.linkedin.com/jobs/view/1234567890

# Génération batch (plusieurs offres)
cd modes/generation_urls_specifique/
nano urls.txt  # Ajoutez vos URLs
./lancer.sh

# Recherche automatique
cd modes/recherche_complete_specifique/
./lancer.sh --poste "Ingénieur IA" --localisation "Paris" --auto top5
```

### Pour Aider Quelqu'un (Profil Générique) 🌍

```bash
cd modes/generation_simple_generique/

# 1. Éditez infos_statique.txt avec les infos de la personne
nano infos_statique.txt

# 2. Lancez la génération
./lancer.sh https://job-url
```

📖 **Voir [DEMARRAGE_RAPIDE.md](DEMARRAGE_RAPIDE.md) pour plus d'exemples**

---

## 📂 Structure du Projet

```
ARCANE/
├── core/                              # 🎯 Cœur du système
│   ├── generateur_cv_lettre.py       # Générateur principal
│   ├── recherche_postes.py            # Recherche multi-plateformes
│   ├── batch_depuis_urls.py           # Génération batch
│   ├── wttj_playwright_scraper.py     # Scraper WTTJ
│   └── config.py                      # Config active
│
├── templates/                         # 📄 Templates LaTeX
│   ├── cv_template.tex                # CV classique
│   ├── cv_template_2col.tex           # CV 2 colonnes
│   └── lettre_motivation_template.tex # Lettre
│
├── modes/                             # 🎭 6 modes d'utilisation
│   ├── recherche_complete_generique/
│   ├── recherche_complete_specifique/
│   ├── generation_urls_generique/
│   ├── generation_urls_specifique/
│   ├── generation_simple_generique/
│   └── generation_simple_specifique/
│
├── documentation/                     # 📚 Documentation
│   ├── GUIDE_MODES.md
│   ├── GUIDE_UTILISATION.txt
│   └── installer_playwright.sh
│
├── candidatures/                      # 📦 Résultats générés
├── venv/                              # 🐍 Environnement Python
├── .env                               # 🔑 Clé API (ignoré par git)
├── requirements.txt                   # 📋 Dépendances
├── README.md                          # 📖 Ce fichier
├── ARCHITECTURE.md                    # 🏗️ Architecture détaillée
└── DEMARRAGE_RAPIDE.md               # ⚡ Guide rapide
```

---

## 🔧 Personnalisation

### Modifier le Template CV

Chaque mode a son propre `config.py` :

```bash
cd modes/generation_simple_specifique/
nano config.py
```

```python
# Changer le template
CV_TEMPLATE = "classique"  # ou "2colonnes"

# Changer le format
CV_FORMAT = "2pages"  # ou "1page"

# Changer les bullets
BULLET_STYLE = "blacksquare"  # ou "bullet", "diamond", etc.
```

### Modifier le Code Source

Le code est dans `core/` :

```bash
cd core/
nano generateur_cv_lettre.py
```

**⚠️ Important :** Les modifications dans `core/` affectent **tous les modes** !

---

## 📊 Exemple de Résultat

Pour chaque candidature, ARCANE génère :

```
candidatures/Ingenieur_IA_TechCorp_20260113/
├── cv.pdf                        # CV personnalisé (1-2 pages)
├── lettre_motivation.pdf         # Lettre ciblée
├── preparation_entretien.txt     # Topo stratégique du poste
├── questions_techniques.txt      # 10 questions tech + réponses
└── questions_personnalite.txt    # 5 questions comportementales STAR
```

---

## 🎓 Documentation Complète

| Document | Description |
|----------|-------------|
| [README.md](README.md) | Ce fichier - Vue d'ensemble |
| [DEMARRAGE_RAPIDE.md](DEMARRAGE_RAPIDE.md) | Guide de démarrage rapide |
| [ARCHITECTURE.md](ARCHITECTURE.md) | Architecture détaillée du système |
| [documentation/GUIDE_MODES.md](documentation/GUIDE_MODES.md) | Guide des modes spécifique/générique |
| [modes/*/README.md](modes/) | Documentation de chaque mode |

---

## 💡 Cas d'Usage

### Scénario 1 : Génération rapide pour vous
```bash
cd modes/generation_simple_specifique/
./lancer.sh https://job-url
```

### Scénario 2 : Recherche pour un ami développeur
```bash
cd modes/recherche_complete_generique/
nano infos_statique.txt  # Ajustez avec ses infos
./lancer.sh --poste "Développeur React" --localisation "Paris" --auto top5
```

### Scénario 3 : Batch de 20 offres
```bash
cd modes/generation_urls_specifique/
nano urls.txt  # Ajoutez 20 URLs
./lancer.sh
```

---

## 🛠️ Technologies Utilisées

- **Python 3.14** - Langage principal
- **Claude Sonnet 4.5** - Modèle IA pour génération
- **LaTeX** - Génération de PDF professionnels
- **BeautifulSoup** - Scraping web
- **Playwright** - Scraping dynamique (WTTJ)
- **Bash** - Scripts d'orchestration

---

## 📝 Licence

MIT License - Voir [LICENSE](LICENSE)

---

## 🤝 Contributions

Les contributions sont les bienvenues ! N'hésitez pas à :
- 🐛 Signaler des bugs
- 💡 Proposer des fonctionnalités
- 📖 Améliorer la documentation
- 🔧 Soumettre des pull requests

---

## 📧 Contact

**Maxime Miroux**  
GitHub: [@Mirouxe](https://github.com/Mirouxe)  
Repository: [ARCANE](https://github.com/Mirouxe/ARCANE)

---

## ⭐ Support

Si vous trouvez ARCANE utile, n'hésitez pas à mettre une étoile ⭐ sur le repository !

---

**🚀 ARCANE : Un cœur, plusieurs visages. Automatisez vos candidatures !**