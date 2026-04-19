# 🎯 Checklist d'Installation - React Frontend ONE DAY ASBL

## ✅ Avant de Commencer

- [ ] Avez-vous Node.js 16+ installé? (Vérifiez : `node --version`)
- [ ] Avez-vous npm installé? (Vérifiez : `npm --version`)
- [ ] Navigateur moderne (Chrome, Firefox, Safari, Edge)

## 🚀 Étapes d'Installation

### Étape 1: Préparer le Dossier (2 min)

```bash
# 1. Naviguez vers le dossier frontend
cd "d:\ONE DAY ASBL\Administratif doc\site one day asbl\frontend"

# 2. Renommez le ancien index.html (optionnel - sauvegarde)
ren index.html index_old.html

# 3. Renommez le nouveau index.html
ren index_new.html index.html
```

### Étape 2: Installer les Dépendances (2 min)

```bash
# Dans le dossier frontend
npm install
```

⏳ Cela prendra 1-2 minutes. Attendez que `added XXX packages` s'affiche.

### Étape 3: Lancer le Serveur de Développement (30 sec)

```bash
npm run dev
```

✨ Votre navigateur s'ouvrira automatiquement sur `http://localhost:3000`

## 🎨 Voir le Site en Action

Vous devriez voir :

1. **Navigation**
   - ✅ Logo "ODA" en vert
   - ✅ Devise "Conscience, Travail et Développement"
   - ✅ Menu responsive

2. **Hero Section**
   - ✅ Slider automatique de 4 photos
   - ✅ Contrôles de navigation (flèches)
   - ✅ Indicateurs en bas

3. **Campagnes**
   - ✅ 6 cartes de campagne
   - ✅ Boutons "J'aime" (❤️), "Commentaire" (💬), "Partager" (📤)
   - ✅ Barre de progression verte

4. **Responsive** (Testez!)
   - Appuyez sur F12 → Toggle device toolbar
   - Vérifiez sur mobile, tablette, desktop

## 🎨 Personnaliser le Site

### Ajouter Votre Logo

Ouvrez `src/components/Navigation.jsx`, ligne 15 :

```jsx
<span className="text-white font-bold text-xl">ODA</span>
// Remplacez "ODA" par votre logo ou une image
```

### Modifier les Campagnes

Ouvrez `src/components/Campaigns.jsx`, ligne 8 :

```javascript
const campaigns = [
  {
    title: "Votre Campagne",
    description: "Description",
    image: "https://url-image.com/image.jpg",
    raised: 50000,
    goal: 100000,
    // ...
  },
];
```

### Changer les Couleurs

Ouvrez `tailwind.config.js` et modifiez le thème des couleurs.

## 📱 Test de Responsivité

```bash
# Depuis votre terminal (le serveur doit tourner)
npm run dev

# Puis ouvrez le DevTools (F12)
# → Cliquez sur l'icône "Toggle device toolbar" (mobile icon)
# → Testez sur différentes tailles
```

## 🔧 Arrêter le Serveur

Appuyez sur `Ctrl + C` dans le terminal.

Pour relancer : `npm run dev`

## 📦 Créer une Version de Production

```bash
# Générer les fichiers optimisés
npm run build

# Prévisualiser avant le déploiement
npm run preview
```

Les fichiers seront dans `dist/`

## 🌐 Déployer en Production

### Option A: Vercel (Recommandé - 2 min)

```bash
npm i -g vercel
vercel
```

### Option B: Netlify (2 min)

1. Allez sur [netlify.com](https://netlify.com)
2. Déposez le dossier `dist/`
3. Terminé!

### Option C: Serveur VPS

```bash
# Générez la build
npm run build

# Copiez le dossier dist/ sur votre serveur
# Servez avec Nginx, Apache, ou un serveur Node.js
```

## 🆘 Dépannage

| Problème                      | Solution                                          |
| ----------------------------- | ------------------------------------------------- |
| **Port 3000 occupé**          | `npm run dev -- --port 3001`                      |
| **Erreur "Module not found"** | `rm -rf node_modules && npm install`              |
| **Site blanc**                | Ouvrez la console (F12) et cherchez les erreurs   |
| **Images ne chargent pas**    | Vérifiez les URLs des images dans `Campaigns.jsx` |
| **Responsive n'est pas bon**  | Videz le cache: Ctrl+Shift+R                      |

## ✅ Checklist Finale

Avant de considérer votre site comme prêt :

- [ ] Le serveur démarre sans erreur
- [ ] La navigation fonctionne (mobile + desktop)
- [ ] Les images du slider se chargent
- [ ] Les boutons d'action sont cliquables
- [ ] Les couleurs sont vertes (émeraude)
- [ ] Le texte "ONE DAY ASBL" est visible
- [ ] La devise est affiché respectueusement
- [ ] Test responsive OK
- [ ] Build de production génère sans erreur

## 📞 Support

Besoin d'aide?

- Consultez `DEPLOYMENT_GUIDE.md`
- Consultez `README_REACT.md`
- Contactez: info@onedayasbl.org

---

**Bravo! Votre site ONE DAY ASBL est maintenant prêt à inspirer le monde! 💚✨**
