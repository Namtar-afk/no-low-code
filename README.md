# 🤖 Workflows d'Automatisation No-Code/Low-Code

Portfolio de 3 projets d'automatisation professionnels démontrant l'orchestration de workflows, l'intégration d'APIs et le développement full-stack.

---

## 📁 Projets

### 1. 📧 [Gmail Automation avec IA](gmail/)
**Système complet d'automatisation Gmail avec analyse IA et dashboard web moderne.**

**Stack** : n8n · OpenAI GPT-3.5-turbo · Docker · Vanilla JavaScript  

**Fonctionnalités** :
- Analyse IA quotidienne des emails (résumé, urgence, priorités)
- Dashboard web responsive avec filtres avancés
- Détection automatique des thèmes clés (1-2 mots)
- Gestion d'emails (épingler, archiver, supprimer)
- Déploiement Docker en 3 commandes

**Accès** :
- 📖 [Documentation complète](gmail/README.md)
- 🌐 Interface web : `http://localhost:8080`
- ⚙️ Workflow n8n : `http://localhost:5678`

---

### 2. 🔄 [Multi-Scraper - Veille IA](multi-scraper/)
**Workflow Make pour agréger du contenu de veille IA depuis multiples sources.**

**Stack** : Make · Google Sheets · OpenAI · Gemini · Apify  

**Fonctionnalités** :
- Agrégation flux RSS IA spécialisés
- Scraping comptes Instagram tech (NVIDIA, OpenAI, Google, etc.)
- Enrichissement IA (résumés, analyse images)
- Export structuré vers Google Sheets
- Déduplication automatique

**Accès** :
- 📖 [Documentation complète](multi-scraper/README.md)
- 🔗 [Google Sheet démo](https://docs.google.com/spreadsheets/d/17JXOTxNk7-EDYpSQIKgBH-hyClpwn7jkmSknl3Azs1A/edit)

---

### 3. 📱 [TikTok Intelligence → Airtable](tiktok/)
**Workflow n8n pour monitorer TikTok et extraire les transcripts vers Airtable.**

**Stack** : n8n · Apify · Airtable · Anthropic · OpenAI  

**Fonctionnalités** :
- Scraping TikTok (mots-clés/comptes) via Apify
- Extraction automatique des sous-titres VTT → transcript
- Analyse IA du contenu vidéo
- Stockage structuré dans Airtable
- Formulaire web pour requêtes

**Accès** :
- 📖 [Documentation complète](tiktok/README.md)

---

## 🚀 Quickstart

| Projet | Installation |
|--------|-------------|
| **Gmail IA** | `cd gmail && docker-compose up -d` → http://localhost:8080 |
| **Multi-Scraper** | Importer `multi-scraper/json/workflow.json` dans Make |
| **TikTok** | Importer `tiktok/json/workflow.json` dans n8n |

## 📊 Structure du dépôt

```
no-low-code/
├── README.md                         # Ce fichier
├── gmail/                            # Gmail Automation
│   ├── docker-compose.yml            # Orchestration Docker
│   ├── json/workflow.json            # Workflow n8n
│   ├── front-page/                   # Interface web
│   │   ├── index.html
│   │   ├── assets/script/script.js
│   │   ├── assets/style/style.css
│   │   └── data/mails-today.json     # Généré par n8n
│   ├── rapport.md                    # Rapport technique
│   ├── screenshots/
│   └── README.md
├── multi-scraper/                    # Multi-Scraper Make
│   ├── json/workflow.json            # Blueprint Make
│   ├── screenshots/
│   └── README.md
└── tiktok/                           # TikTok Scraper
    ├── json/workflow.json            # Workflow n8n
    ├── screenshots/
    └── README.md
```

## 🛠️ Technologies

### Automation & Orchestration
- **n8n** : Workflow automation open-source (Gmail, TikTok)
- **Make** : Automatisation visuelle (Multi-Scraper)
- **Docker** : Conteneurisation et déploiement

### Intelligence Artificielle
- **OpenAI GPT-3.5-turbo** : Analyse emails, enrichissement contenu
- **Google Gemini Pro** : Analyse d'images Instagram
- **Anthropic Claude** : Analyse vidéos TikTok

### APIs & Intégrations
- **Gmail API** : Récupération emails
- **Apify** : Web scraping (Instagram, TikTok)
- **Airtable** : Base de données structurée
- **Google Sheets** : Stockage et reporting

### Frontend
- **Vanilla JavaScript** : Interface web performante (sans framework)
- **HTML5 / CSS3** : Design moderne et responsive
- **Lucide Icons** : Iconographie

## 🎯 Cas d'usage

| Projet | Cas d'usage |
|--------|------------|
| **Gmail Automation** | Gestion intelligente des emails, priorisation automatique, résumés quotidiens IA |
| **Multi-Scraper** | Veille concurrentielle IA, agrégation multi-sources, monitoring tech |
| **TikTok Scraper** | Social media monitoring, extraction de tendances, analyse de contenu |

## 🎓 Compétences démontrées

### Backend & Automation
- Orchestration de workflows (n8n, Make)
- Intégration d'APIs tierces (Gmail, OpenAI, Apify, Airtable)
- Gestion de credentials et secrets
- Error handling et retry logic
- Parsing et transformation de données

### Frontend
- Développement web vanilla (HTML5, CSS3, JavaScript)
- Design responsive et accessible
- Gestion d'état côté client (localStorage)
- Optimisation des performances (cache busting, lazy rendering)

### DevOps
- Conteneurisation Docker
- Docker Compose multi-services
- Gestion de volumes partagés
- Configuration environnement reproductible

### IA & LLM
- Prompt engineering (OpenAI, Anthropic, Gemini)
- Parsing robuste de sortie LLM
- Gestion des formats JSON structurés
- Fine-tuning des paramètres (temperature, tokens)

### Architecture
- Architecture microservices
- Séparation backend/frontend
- Flux de données asynchrones
- Design modulaire et maintenable

## 🔐 Bonnes pratiques

✅ **Sécurité** : Credentials dans gestionnaires dédiés (n8n Credentials, Make Connections)  
✅ **Rate Limiting** : Respect des quotas API (Gmail, OpenAI, Apify)  
✅ **Error Handling** : Try/catch, retry logic, fallbacks  
✅ **Documentation** : README complets, commentaires, rapports techniques  
✅ **Versionning** : Exports réguliers des workflows, Git pour le code  
✅ **Monitoring** : Logs Docker, historique d'exécutions n8n/Make  

## 📖 Documentation

Chaque projet dispose de sa documentation complète :
- **Architecture** : Schémas et flux de données
- **Installation** : Guide pas-à-pas pour recruteurs
- **Configuration** : Credentials et paramètres
- **Utilisation** : Cas d'usage et exemples
- **Dépannage** : Erreurs courantes et solutions
- **Captures d'écran** : Interfaces et résultats

## 🚧 Défis techniques résolus

### Gmail Automation
1. **Parsing LLM** : Gestion robuste du JSON généré par OpenAI avec multiples formats
2. **Synchronisation n8n-frontend** : Branchement correct webhook/manual/schedule
3. **Volumes Docker** : Partage de données entre conteneurs n8n et web

### Multi-Scraper
1. **Agrégation multi-sources** : Normalisation de formats hétérogènes (RSS, Instagram)
2. **Déduplication** : Éviter les doublons dans Google Sheets
3. **Enrichissement IA** : Analyse d'images avec Gemini Pro

### TikTok Scraper
1. **Extraction VTT** : Parsing des sous-titres et nettoyage timestamps
2. **Rate limiting** : Gestion des quotas Apify et TikTok
3. **Formulaire dynamique** : Génération de requêtes depuis interface web

---

## 👤 Contact

**Roméo Cavazza**  
📧 [romeo.cavazza@gmail.com](mailto:romeo.cavazza@gmail.com)  
💼 [LinkedIn](https://www.linkedin.com/in/romeo-cavazza/)  
💻 [GitHub](https://github.com/RomeoCavazza)

---

*3 workflows d'automatisation professionnels - Prêts à déployer et personnaliser*
