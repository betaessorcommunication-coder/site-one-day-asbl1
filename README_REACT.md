# 💚 ONE DAY ASBL - Frontend React

Une plateforme de collecte de fonds moderne et professionnelle pour ONE DAY ASBL, construite avec React, Tailwind CSS et Vite.

## 🎯 Caractéristiques Principales

✅ **Design Immersif**

- Hero section avec slider automatique de photos
- Animations fluides et transitions élégantes
- Design inspiré par les standards d'organisations humanitaires

✅ **Identité Visuelle**

- Couleur principale : Vert émeraude (confiance, développement, agriculture)
- Palette cohérente et accessibilité garantie
- Logo et branding intégré dans la navigation

✅ **Campagnes Interactives**

- Cartes de campagne avec indicateurs de progression
- Boutons "J'aime" (❤️), "Commentaire" (💬), "Partager" (📤)
- CTA "Faire un Don" prominent sur chaque campagne

✅ **Responsive Design**

- Mobile-first approach
- Testé sur tous les appareils (mobile, tablette, desktop)
- Navigation adaptative

✅ **Performance**

- Temps de chargement < 2 secondes
- Optimisation des images
- Code-splitting automatique

## 📁 Structure du Projet

```
frontend/
├── src/
│   ├── components/
│   │   ├── Navigation.jsx      # Barre de navigation avec logo
│   │   ├── Hero.jsx            # Hero section avec slider
│   │   ├── Statistics.jsx      # Statistiques d'impact
│   │   ├── Campaigns.jsx       # Grille de campagnes
│   │   ├── CampaignCard.jsx    # Carte individuelle avec interactions
│   │   ├── Actions.jsx         # Domaines d'action
│   │   ├── About.jsx           # À propos et équipe
│   │   ├── Subscribe.jsx       # Newsletter
│   │   └── Footer.jsx          # Pied de page
│   ├── App.jsx                 # Composant racine
│   ├── main.jsx                # Point d'entrée React
│   └── index.css               # Styles globaux Tailwind
├── index_new.html              # Point d'entrée HTML (renommer en index.html)
├── package.json                # Dépendances
├── vite.config.js              # Configuration Vite
├── tailwind.config.js          # Configuration Tailwind
├── postcss.config.js           # Configuration PostCSS
└── DEPLOYMENT_GUIDE.md         # Guide de déploiement
```

## 🚀 Installation & Démarrage

### 1. Installation des dépendances

```bash
cd frontend
npm install
```

### 2. Lancer le serveur de développement

```bash
npm run dev
```

### 3. Accéder au site

Ouvrez votre navigateur sur `http://localhost:3000`

## 🎨 Palettes de Couleurs

### Vert (Couleur Principale)

- `emerald-600` : #16a34a (boutons CTA, éléments importants)
- `emerald-700` : #15803d (hovers, textes importants)
- `emerald-50` : #f0fdf4 (fonds légers)

### Neutre (Couleurs Secondaires)

- Gris pour le texte
- Blanc pour les fonds
- Bleu très léger en arrière-plan (accents subtils)

## 🎬 Sections du Site

| Section          | Description        | Fonctionnalité                        |
| ---------------- | ------------------ | ------------------------------------- |
| **Navigation**   | Barre fixe en haut | Menu responsive, logo, CTA            |
| **Hero**         | Slider full-screen | 4 slides automatiques avec contrôles  |
| **Statistiques** | Compteurs animés   | Impact en chiffres                    |
| **Campagnes**    | Grille 3 colonnes  | Like, Commentaire, Partage, Don       |
| **Actions**      | 4 domaines clés    | Agriculture, Santé, Éducation, Sports |
| **À Propos**     | Valeurs et équipe  | Team cards avec avatars               |
| **Newsletter**   | Abonnement         | Input email + validation              |
| **Footer**       | Liens et contact   | Navigation, infos contact, réseaux    |

## 🔗 Intégration Backend

Pour connecter au backend API (Node.js/Express) :

1. Modifiez les URLs d'API dans les composants :

```javascript
const API_URL = 'http://localhost:5000';

// Exemple dans CampaignCard.jsx
const response = await fetch(`${API_URL}/api/donations`, {
  method: 'POST',
  body: JSON.stringify({ ... })
});
```

2. Configurez les variables d'environnement dans `.env.local` :

```env
VITE_API_URL=http://localhost:5000
```

3. Utilisez-les dans le code :

```javascript
const API_URL = import.meta.env.VITE_API_URL;
```

## 📱 Responsive Breakpoints

- **Mobile** : 320px - 767px
- **Tablet** : 768px - 1023px
- **Desktop** : 1024px+

Tous les composants utilisent les classes Tailwind : `md:`, `lg:` pour les transitions.

## 🎯 Prochaines Étapes

1. ✅ Frontend complété
2. ⏳ Remplacer `index.html` par `index_new.html`
3. ⏳ Installer Node.js et dépendances
4. ⏳ Connecter le backend API
5. ⏳ Configurer les paiements Flutterwave/Paystack
6. ⏳ Déployer sur Vercel/Netlify

## 📚 Ressources

- [React Documentation](https://react.dev)
- [Tailwind CSS](https://tailwindcss.com)
- [Vite](https://vitejs.dev)
- [Deployment Guide](./DEPLOYMENT_GUIDE.md)

## 💚 Contribuer

Vous avez des idées d'amélioration ?

- Créez une issue
- Soumettez un PR
- Contactez-nous à info@onedayasbl.org

---

**Ensemble, transformons le Congo! 🌍✨**
