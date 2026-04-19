# 🚀 DÉMARREZ MAINTENANT! (3 étapes - 5 minutes)

## ⏱️ Temps Total: ~5 minutes

### ÉTAPE 1️⃣: Préparer les Fichiers (1 min)

Ouvrez l'explorateur Windows et allez à:

```
d:\ONE DAY ASBL\Administratif doc\site one day asbl\frontend\
```

Renommez le fichier:

- **De:** `index_new.html`
- **À:** `index.html`

_(Vous pouvez sauvegarder l'ancien dans un dossier "backup" si vous voulez)_

### ÉTAPE 2️⃣: Installer (2-3 min)

Ouvrez **PowerShell** ou **Command Prompt** et exécutez:

```bash
cd "d:\ONE DAY ASBL\Administratif doc\site one day asbl\frontend"
npm install
```

⏳ **Attendez** 2-3 minutes. Vous verrez "added XXX packages" à la fin.

### ÉTAPE 3️⃣: Lancer (30 sec)

```bash
npm run dev
```

✨ **Voilà!** Votre navigateur s'ouvre automatiquement sur:

```
http://localhost:3000
```

---

## 👀 Qu'allez-vous Voir?

### 🎨 Design

- **Couleur dominante**: Vert émeraude (#16a34a)
- **Logo**: Rond vert "ODA" en haut
- **Devise**: "Conscience, Travail et Développement" à côté du logo

### 🖼️ Hero Section

- **Slider automatique** avec 4 belles photos
- Les photos changent toutes les 5 secondes
- Navigation par flèches (◀ ▶) en bas

### 💚 Campagnes

- **6 cartes** avec images
- Chaque carte a:
  - ❤️ Bouton "J'aime" (clic → le cœur devient rouge)
  - 💬 Bouton "Commentaire" (clic → affiche des commentaires)
  - 📤 Bouton "Partager" (clic → partage Web API)
  - 💚 Gros bouton **FAIRE UN DON** en vert

### 📱 Responsive

- **Redimensionnez** la fenêtre
- L'interface s'adapte automatiquement au mobile/tablette/desktop
- Testez avec **F12** → icône mobile

---

## 🎯 Navigation du Site

| Section          | Description                   |
| ---------------- | ----------------------------- |
| **Navigation**   | Menu fixe en haut avec logo   |
| **Hero**         | Slider photo + devise + CTA   |
| **Statistiques** | 4 compteurs animés            |
| **Campagnes**    | 6 campagnes avec interactions |
| **Actions**      | 4 domaines clés (🌾🏥📚⚽)    |
| **À Propos**     | Équipe + valeurs              |
| **Newsletter**   | S'abonner aux nouvelles       |
| **Footer**       | Contact + liens               |

---

## 🎨 Tester les Interactions

### Tester le "J'aime"

1. Allez à la section **Campagnes**
2. Cliquez sur ❤️ sur une campagne
3. Le cœur devient rouge et le nombre augmente
4. Clic à nouveau → le cœur redevient blanc

### Tester le "Partager"

1. Cliquez sur 📤
2. Une fenêtre de partage Web API s'ouvre (sur mobile)
3. Sur desktop → alerte "Campagne partagée!"

### Tester le "Commentaire"

1. Cliquez sur 💬
2. Une section commentaires s'affiche
3. Cliquez à nouveau pour la masquer

### Tester le Slider

1. Le slider change automatiquement ses photos
2. Ou cliquez sur les flèches ◀ ▶
3. Ou cliquez sur les points en bas

---

## ⚙️ Si Vous Avez des Problèmes

### ❌ Erreur: "npm not found"

```bash
# Installez Node.js depuis:
# https://nodejs.org/

# Puis relancez PowerShell et réessayez
npm --version
```

### ❌ Port 3000 déjà utilisé

```bash
# Utilisez un autre port:
npm run dev -- --port 3001
# Puis allez à http://localhost:3001
```

### ❌ Site blanc après démarrage

1. Ouvrez **F12** (DevTools)
2. Vérifiez s'il y a des erreurs en rouge dans la console
3. Si vous voyez une erreur, prenez une capture d'écran
4. Contactez le support

### ❌ Les images ne chargent pas

- C'est normal au premier lancement
- Attendez quelques secondes
- Les images viennent d'URLs externes (Unsplash)
- Si le problème persiste, vérifiez votre connexion Internet

---

## 📝 Personnaliser Rapidement

### Changer le Titre du Site

Ouvrez `frontend/index.html` et modifiez la ligne:

```html
<title>ONE DAY ASBL | Conscience, Travail et Développement</title>
```

### Changer les Campagnes Affichées

Ouvrez `frontend/src/components/Campaigns.jsx` et modifiez le tableau `campaigns` (ligne 8).

### Ajouter Votre Logo Réel

Ouvrez `frontend/src/components/Navigation.jsx` et remplacez:

```jsx
<span className="text-white font-bold text-xl">ODA</span>
```

Par une balise `<img>` avec votre logo.

---

## 🚀 Déployer en Production

Une fois satisfait, déployez gratuitement sur:

### Option A: Vercel (1 min)

```bash
npm i -g vercel
cd frontend
vercel
```

Puis votre site sera sur `https://one-day-asbl.vercel.app`

### Option B: Netlify (5 min)

1. Allez sur [netlify.com](https://netlify.com)
2. Glissez-déposez le dossier `frontend/dist/`
3. Voilà! Votre site est en ligne

### Option C: Railway (3 min)

1. Allez sur [railway.app](https://railway.app)
2. Connectez votre GitHub
3. Déployez automatiquement

**Consultez `DEPLOYMENT_COMPLETE.md` pour plus de détails.**

---

## 📞 Questions?

Souvenez-vous des fichiers de documentation:

- 📋 `INSTALLATION_CHECKLIST.md` → Guide pas-à-pas
- 🚀 `DEPLOYMENT_GUIDE.md` → Comment déployer
- 📖 `README_REACT.md` → Documentation complète
- 🎯 `REFONTE_REACT_RESUME.md` → Vue d'ensemble

---

## ✅ Checklist Rapide

- [ ] Renommé `index_new.html` → `index.html`
- [ ] Installé avec `npm install`
- [ ] Lancé avec `npm run dev`
- [ ] Navigateur ouvert sur `http://localhost:3000`
- [ ] Vu le slider avec 4 photos
- [ ] Cliqué sur ❤️ pour tester
- [ ] Cliqué sur 📤 pour tester le partage
- [ ] Redimensionné la fenêtre pour tester mobile
- [ ] Vu les couleurs vertes

---

**🎉 Bravo! Votre site ONE DAY ASBL est maintenant LIVE!**

**💚 Ensemble, transformons le Congo!**
