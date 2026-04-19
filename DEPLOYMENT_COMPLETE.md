# 🚀 DÉPLOIEMENT COMPLET ONE DAY ASBL

## 🎯 Vue d'Ensemble du Déploiement

Votre plateforme complète ONE DAY ASBL se compose de 3 parties :

```
┌─────────────────────────────────────────────────────────┐
│  FRONTEND (React + Tailwind)  - Port 3000              │
│  └─ Site web public avec slider, campagnes, interactivité
├─────────────────────────────────────────────────────────┤
│  BACKEND (Node.js + Express)  - Port 5000              │
│  └─ API pour donations, paiements, gestion des campagnes
├─────────────────────────────────────────────────────────┤
│  DATABASE (MongoDB)                                     │
│  └─ Stockage des campagnes, donations, utilisateurs
└─────────────────────────────────────────────────────────┘
```

## 🏠 Déploiement Local (30 secondes)

### Prérequis

- Node.js 16+
- MongoDB (local ou cloud)
- Docker (optionnel)

### Étape 1: Frontend

```bash
cd frontend
npm install
npm run dev
# Accessible sur http://localhost:3000
```

### Étape 2: Backend

```bash
cd ../backend
npm install
npm start
# Accessible sur http://localhost:5000
```

### Étape 3: Tester la Connexion

```bash
# Testez l'API
curl http://localhost:5000/api/campaigns
# Devrait retourner un JSON
```

## 🐳 Déploiement avec Docker

### Avantage

Une seule commande lance frontend + backend + base de données!

### Prérequis

- Docker Desktop installé

### Commande de Déploiement

```bash
# À la racine du projet
docker-compose up -d

# Vérifiez les conteneurs
docker-compose ps

# Consultez les logs
docker-compose logs backend
docker-compose logs frontend
```

Puis :

- Frontend: http://localhost:3000
- Backend: http://localhost:5000

### Arrêter les Services

```bash
docker-compose down
```

## ☁️ Déploiement en Production

### Architecture Recommandée

```
Internet
   ↓
CDN (Cloudflare) [Optionnel]
   ↓
Serveur Frontend (Vercel/Netlify)  →  Serveur Backend (Heroku/Railway)
                                    →  Base de Données (MongoDB Atlas)
```

---

## 🌐 Option 1: Vercel + Heroku + MongoDB Atlas (Gratuit)

### 1️⃣ MongoDB Atlas (Base de Données Cloud)

```bash
# 1. Créez un compte sur mongodb.com/cloud/atlas
# 2. Créez un cluster
# 3. Récupérez l'URL de connexion:
# mongodb+srv://user:password@cluster.mongodb.net/one-day-asbl

# 4. Définissez la variable d'environnement
# MONGODB_URI=mongodb+srv://...
```

### 2️⃣ Backend sur Heroku

```bash
# 1. Installez Heroku CLI
# 2. Authentifiez-vous
heroku login

# 3. Créez une app Heroku
heroku create one-day-asbl-api
# Récupérez: one-day-asbl-api.herokuapp.com

# 4. Configurez les variables d'environnement
heroku config:set MONGODB_URI=mongodb+srv://...
heroku config:set JWT_SECRET=votre_secret_key
heroku config:set FLUTTERWAVE_KEY=votre_clé

# 5. Déployez
cd backend
git push heroku main
# ou si pas de git: heroku deploy (avec Docker)

# 6. Vérifiez
heroku logs --tail
curl https://one-day-asbl-api.herokuapp.com/api/campaigns
```

### 3️⃣ Frontend sur Vercel

```bash
# 1. Installez Vercel CLI
npm i -g vercel

# 2. Déployez
cd frontend
vercel

# 3. Configurez les variables d'environnement
# Pendant le déploiement ou dans le dashboard Vercel
# VITE_API_URL=https://one-day-asbl-api.herokuapp.com

# 4. Votre site en ligne! 🎉
# https://one-day-asbl.vercel.app
```

---

## 🚀 Option 2: Railway (Tout-en-un - Recommandé)

Railway gère frontend + backend + database en un seul endroit!

### Étapes

```bash
# 1. Créez un compte sur railway.app
# 2. Connectez votre GitHub
# 3. Créez un nouveau projet
# 4. Ajoutez un service MongoDB
# 5. Déployez le backend depuis le repo
# 6. Déployez le frontend depuis le repo

# Railway génère automatiquement les URLs:
# - Backend: https://one-day-api.railway.app
# - Frontend: https://one-day-frontend.railway.app
# - MongoDB: Variable MONGO_URL auto-configurée
```

---

## 🔐 Option 3: VPS Linux (Full Control)

Pour un contrôle complet (Ubuntu 20.04+) :

```bash
# 1. Installez Node.js et npm
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# 2. Installez MongoDB
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -
sudo apt-get install -y mongodb

# 3. Configurez Nginx
sudo apt-get install -y nginx

# 4. Clonez le projet
git clone https://github.com/your-org/one-day-asbl.git
cd one-day-asbl

# 5. Installez les dépendances
cd frontend && npm install && npm run build
cd ../backend && npm install

# 6. Configurez les variables d'environnement
cp .env.example .env
# Modifiez .env avec vos clés

# 7. Utilisez PM2 pour garder les services actifs
sudo npm i -g pm2
pm2 start backend/src/server.js --name "one-day-api"
pm2 save
pm2 startup

# 8. Configurez Nginx pour servir le frontend
sudo nano /etc/nginx/sites-available/one-day-asbl
# Voir config ci-dessous
```

### Configuration Nginx

```nginx
upstream backend {
    server localhost:5000;
}

server {
    listen 80;
    server_name one-day-asbl.cd www.one-day-asbl.cd;

    # Frontend (React)
    location / {
        root /path/to/frontend/dist;
        try_files $uri $uri/ /index.html;
    }

    # API Backend
    location /api/ {
        proxy_pass http://backend;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
    }

    # SSL (avec Let's Encrypt)
    listen 443 ssl;
    ssl_certificate /etc/letsencrypt/live/one-day-asbl.cd/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/one-day-asbl.cd/privkey.pem;
}
```

---

## 📊 Environnements & Variables

### Variables Critiques

```env
# BASE DE DONNÉES
MONGODB_URI=mongodb+srv://user:pass@cluster.mongodb.net/one-day

# JWT & Sécurité
JWT_SECRET=votre_super_secret_long_et_complexe
NODE_ENV=production

# PAIEMENTS
FLUTTERWAVE_SECRET_KEY=sk_live_...
PAYSTACK_SECRET_KEY=sk_live_...

# FRONTEND API
VITE_API_URL=https://api.one-day-asbl.cd
```

### Configuration par Environnement

| Variable   | Dev                   | Production                  |
| ---------- | --------------------- | --------------------------- |
| NODE_ENV   | development           | production                  |
| DB         | localhost:27017       | MongoDB Atlas               |
| API_URL    | http://localhost:5000 | https://api.one-day-asbl.cd |
| LOG_LEVEL  | debug                 | error                       |
| RATE_LIMIT | 1000/min              | 100/min                     |

---

## ✅ Checklist de Déploiement Production

### Avant le Lancement

- [ ] Base de données migrée vers MongoDB Atlas
- [ ] Toutes les variables d'environnement configurées
- [ ] Certificat SSL installez (https://)
- [ ] Domaine DNS pointant vers le serveur
- [ ] Backups automatiques activés
- [ ] CORS configuré correctement
- [ ] Logs centralisés (optional: Sentry)
- [ ] Monitoring activé
- [ ] Tests de charge réussis

### Après le Lancement

- [ ] Site accessible sur le domaine public
- [ ] API répondant correctement
- [ ] Paiements en mode test
- [ ] Emails de notification fonctionnels
- [ ] Analytics installés (Google Analytics)
- [ ] Monitoring 24/7
- [ ] Runbook de secours préparé

---

## 🔄 CI/CD Pipeline (Automatique)

Avec GitHub Actions (gratuit) :

```yaml
# .github/workflows/deploy.yml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy Backend
        run: |
          # Votre script de déploiement
          heroku deploy
      - name: Deploy Frontend
        run: |
          cd frontend
          vercel deploy --prod
```

---

## 💚 Monitoring en Production

### Outils Recommandés

1. **Uptime** : UptimeRobot (gratuit)
2. **Logs** : Papertrail ou Sentry
3. **Analytics** : Google Analytics
4. **Erreurs** : Sentry (gratuit tier)
5. **Performance** : New Relic (gratuit tier)

### Commandes de Monitoring Basiques

```bash
# Vérifier l'API
curl https://api.one-day-asbl.cd/api/status

# Vérifier les logs backend
pm2 logs one-day-api

# Vérifier la base de données
mongosh --uri "mongodb+srv://..."
```

---

## 🆘 Troubleshooting Déploiement

| Erreur                 | Cause                                | Solution                            |
| ---------------------- | ------------------------------------ | ----------------------------------- |
| `Cannot connect to DB` | URL MongoDB incorrecte               | Vérifiez MONGODB_URI                |
| `CORS Error`           | Frontend/Backend domaines différents | Configurez CORS dans backend        |
| `Port already in use`  | Autre service sur le port            | `lsof -i :5000` + kill              |
| `Asset 404`            | Frontend build manquée               | `npm run build` puis vérifiez dist/ |
| `Payment failed`       | Clé API incorrecte                   | Testez en mode sandbox d'abord      |

---

## 📞 Support & Escalade

- 📧 **Dev Issues**: dev@one-day-asbl.org
- 📱 **Urgent**: +243 XXX XXX XXX
- 🔗 **Repo**: https://github.com/... (coming soon)
- 📦 **Docs**: /docs/

---

## 🎯 Timeline de Déploiement Proposé

**Semaine 1** : Setup local + tests
**Semaine 2** : Déploiement test sur [Railway](https://railway.app)
**Semaine 3** : Configurations paiements + domaine
**Semaine 4** : Lancement production + monitoring

---

**🚀 Bon courage pour le déploiement! Ensemble, on va changer le Congo! 💚✨**
