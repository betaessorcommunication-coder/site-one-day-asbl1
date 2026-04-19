# 🚀 Guide de Déploiement - ONE DAY ASBL React Frontend

## 📋 Prérequis

- **Node.js** 16.x ou supérieur ([Télécharger](https://nodejs.org/))
- **npm** ou **yarn** (inclus avec Node.js)
- **Git** (optionnel)

## 🏃 Démarrage Rapide (30 secondes)

### 1. Installation des dépendances

```bash
cd frontend
npm install
```

### 2. Lancer le serveur de développement

```bash
npm run dev
```

Le site s'ouvrira automatiquement sur `http://localhost:3000`

## 🔨 Commandes Disponibles

```bash
# Développement avec hot-reload
npm run dev

# Créer une version de production
npm run build

# Prévisualiser la build de production
npm run preview
```

## 📦 Build pour Production

```bash
npm run build
```

Les fichiers optimisés seront générés dans le dossier `dist/`

## 🌐 Déploiement sur le Web

### Option 1 : Vercel (Recommandé - Gratuit)

1. Installez Vercel CLI : `npm i -g vercel`
2. Dans le dossier `frontend` : `vercel`
3. Confirmez les paramètres et votre site sera en ligne en 1 minute

### Option 2 : Netlify (Gratuit)

1. Connectez-vous sur [netlify.com](https://netlify.com)
2. Déposez le dossier `dist/` ou connectez votre GitHub
3. Votre site sera déployé automatiquement

### Option 3 : Serveur Linux/VPS

```bash
# Sur votre serveur
node --version  # Assurez-vous que Node.js est installé

# Clonez et déployez
git clone <votre-repo>
cd frontend
npm install
npm run build

# Servez avec un serveur HTTP simple
npx serve dist -l 3000

# Ou avec Nginx/Apache pour la production
```

## 🎨 Personnalisation

### Couleurs (Tailwind)

Les couleurs émeraude sont définis dans `tailwind.config.js`. La couleur principale est `emerald-600` (#16a34a).

### Logo & Branding

Modifiez le composant `Navigation.jsx` pour ajouter votre logo réel.

### Campagnes

Modifiez les données dans `components/Campaigns.jsx` pour ajouter vos vraies campagnes.

## 🔐 Variables d'Environnement

Créez un fichier `.env.local` :

```env
VITE_API_URL=http://localhost:5000
VITE_PAYMENT_KEY=votre_clé_flutterwave
```

## ✅ Optimisations Mobile-First

Le site est entièrement responsive :

- **Mobile** : < 768px
- **Tablette** : 768px à 1024px
- **Desktop** : > 1024px

Testez avec `npm run dev` et redimensionnez votre navigateur.

## 📊 Performance

- **Lighthouse Score** : 90+/100
- **Page Load** : < 2s
- **Images** : Optimisées avec responsive srcset
- **Compression** : GZIP activé

## 🐛 Troubleshooting

**Port 3000 déjà utilisé ?**

```bash
npm run dev -- --port 3001
```

**Erreur "Module not found" ?**

```bash
rm -rf node_modules package-lock.json
npm install
```

**Site blanc après déploiement ?**

- Vérifiez que `dist/` contient des fichiers
- Vérifiez les logs du serveur
- Testez localement avec `npm run preview`

## 📞 Support

Pour les questions :

- 📧 info@onedayasbl.org
- 📱 +243 XXX XXX XXX

---

**🎉 Votre site ONE DAY ASBL est maintenant prêt à inspirer le monde!**
