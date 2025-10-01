# Workflow n8n - Gmail Automation

## 🎯 Fonction
Workflow n8n pour récupérer les emails Gmail, les analyser avec OpenAI GPT-3.5-turbo, et générer un JSON exploitable.

## 🏗️ Architecture

```
Trigger (Schedule/Webhook/Manual)
    ↓
Gmail API - Get Messages (24h, hors promotions)
    ↓
Extract & Clean Data (JavaScript)
    ↓
OpenAI Analysis → JSON Summary
    ↓
Merge Results → Convert to Binary
    ↓
Write File → /files/mails-today.json
```

## 📊 Déclencheurs

- **Schedule** : Automatique quotidien à 18h00
- **Webhook** : `/webhook/refresh-mails` (depuis l'interface)
- **Manual** : Bouton "Test workflow" dans n8n

## 🔧 Configuration

### Credentials requises

**1. Gmail OAuth2**
- Scope : `gmail.readonly`
- URI redirection : `http://localhost:5678/rest/oauth2-credential/callback`

**2. OpenAI**
- Model : `gpt-3.5-turbo`
- Temperature : 0.7

### Paramètres du workflow

**Gmail query** : `newer_than:1d -category:promotions`  
**Output path** : `/files/mails-today.json`  
**Webhook path** : `/webhook/refresh-mails`

## 📤 Format de sortie

```json
{
  "day": "2025-10-01",
  "total": 15,
  "urgency_level": "moyenne",
  "tl_dr": "Résumé personnalisé...",
  "priority_emails": [
    {"id": "abc", "reason": "Réponse recruteur"}
  ],
  "key_topics": ["emploi", "sécurité"],
  "suggested_actions": ["Répondre au recruteur"],
  "emails": [...]
}
```

## 🚀 Installation

### 1. Import dans n8n
1. Ouvrir n8n : http://localhost:5678
2. Menu → **Import from File**
3. Sélectionner `json/workflow.json`

### 2. Configurer Gmail OAuth2

#### Prérequis : Google Cloud Console
1. Créer un projet sur [Google Cloud Console](https://console.cloud.google.com/)
2. Activer **Gmail API**
3. Créer **OAuth 2.0 Client ID** (Web application)
4. **⚠️ IMPORTANT - Authorized JavaScript origins :**
   ```
   http://localhost:5678
   ```
5. **⚠️ IMPORTANT - Authorized redirect URIs :**
   ```
   http://localhost:5678/rest/oauth2-credential/callback
   ```
6. **OAuth consent screen** → Ajouter scope :
   ```
   https://www.googleapis.com/auth/gmail.readonly
   ```

#### Dans n8n
1. Cliquer sur le nœud **"Get many messages"**
2. Credential → **Create New**
3. Coller Client ID + Client Secret
4. **Connect my account** → Autoriser Gmail

### 3. Configurer OpenAI

#### Créer une clé API
1. Aller sur [OpenAI Platform](https://platform.openai.com/api-keys)
2. **+ Create new secret key**
3. Copier la clé immédiatement

#### Dans n8n
1. Cliquer sur le nœud **"Basic LLM Chain"**
2. Credential → **Create New**
3. Coller l'API Key

### 4. Préparer les permissions d'écriture
**⚠️ CRITIQUE :** Sans cette étape, vous aurez l'erreur "Forbidden by access permissions"

```bash
cd /chemin/vers/no-low-code/gmail
docker run --rm -v "$(pwd)/front-page/data:/data" alpine sh -c "chmod -R 777 /data"
```

### 5. Test
1. Cliquer **"Test workflow"**
2. Attendre 30-60 secondes
3. Vérifier qu'il n'y a pas d'erreur
4. Vérifier la création du fichier :
   ```bash
   cat front-page/data/mails-today.json
   ```

### 6. Activation
Toggle **"Active"** → ON (bleu)  
→ Exécution automatique tous les jours à 18h00

## 🐛 Dépannage

**LLM retourne null**  
→ Vérifier connexion "Basic LLM Chain" → "Merge Results"

**JSON parsing failed**  
→ Vérifier le prompt et température (0.7)

**File not found**  
→ Vérifier volume Docker : `./front-page/data:/files`
→ Vérifier permissions : `chmod -R 777 ./front-page/data` via conteneur Docker

**Gmail quota exceeded**  
→ Espacer les exécutions, vérifier quotas Google Cloud

## 📊 Monitoring

```bash
# Logs
docker-compose logs -f n8n

# Test webhook
curl -X POST http://localhost:5678/webhook/refresh-mails
```

---
*Workflow n8n robuste - Prêt pour production*
