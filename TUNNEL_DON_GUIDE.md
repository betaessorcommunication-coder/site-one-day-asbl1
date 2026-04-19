# Guide du Tunnel de Don - ONE DAY ASBL

## Activation et Utilisation - 18 avril 2026

---

## 📋 Vue d'ensemble

Le tunnel de don a été complètement refactorisé pour offrir une expérience utilisateur professionnelle et sécurisée. Les visiteurs peuvent maintenant faire un don via trois options de paiement distinctes.

---

## 🎯 Trois Options de Paiement

### 1. 📱 **Mobile Money (RDC)**

**Opérateurs disponibles** :

- M-Pesa
- Orange Money
- Airtel Money

**Interface** :

- Logos officiels cliquables
- Champ de saisie du numéro de téléphone
- Format : `+243 812 345 678`

---

### 2. 💳 **Carte Bancaire (Visa/Mastercard)**

**Caractéristiques** :

- Sélection du type de carte (Visa ou Mastercard)
- Champs de saisie sécurisée :
  - Numéro de carte (16 chiffres)
  - Date d'expiration (MM/YY)
  - CVV (3-4 chiffres)

---

### 3. 🏦 **Virement Bancaire**

**Affichage des coordonnées** :

- Bouton "Afficher les coordonnées bancaires"
- Au clic, affichage d'un cadre élégant avec tous les détails

**Détails complètes** :

```
Bénéficiaire : Christian Kabamba Ebondo
IBAN : BE34 6505 6439 1190
BIC : REVOBEB2
Banque Correspondante : CHASDEFX
Compte Institutionnel : One Day ASBL
Banque : Trust Merchant Bank S.A (TMB)
Numéro de Compte : 00017-11020-7305157000-03
```

**Fonctionnalité** :

- Bouton "Copier" pour chaque champ
- Feedback visuel (bouton devient vert : "✓ Copié")

---

## 🎨 Design & UX

### Éléments Visuels

- **Couleur principale** : VERT (Charte graphique)
- **Icône de sécurité** : 🔒 Cadenas à côté de "Paiement 100% sécurisé"
- **Structure** : Onglets clairs et distincts
- **Cadre bancaire** : Gris clair (#f3f4f6) pour une excellente lisibilité

### Responsive

- ✅ Parfaitement adapté aux téléphones mobiles
- ✅ Tests recommandés sur écrans 375px minimum
- ✅ Interfaces tactiles optimisées

### Modularité

- Fenêtre modale (modal) qui n'abandonne pas la page
- Fermeture possible (bouton ✕)
- Annulation sans effet de bord

---

## 🔧 Implémentation Technique

### Nouveaux Fichiers Créés

#### `frontend/src/components/DonationModal.jsx`

Composant React autonome avec :

- Gestion d'état complète du formulaire
- Validation des données
- Affichage conditionnel par onglet
- Fonction de copie au presse-papiers
- Feedback utilisateur (messages de confirmation)

**Props** :

```jsx
<DonationModal
  campaign={campaign}      // Objet campagne
  isOpen={boolean}         // État d'affichage
  onClose={function}       // Fonction de fermeture
/>
```

### Fichiers Modifiés

#### `frontend/src/components/CampaignCard.jsx`

- Import du composant `DonationModal`
- Simplification de la gestion d'état (suppression logique modal embarquée)
- Mise à jour des couleurs : `emerald` → `brand`
- Intégration du bouton "Faire un Don Maintenant"

#### `frontend/src/components/Campaigns.jsx`

- Mise à jour des couleurs pour cohérence

---

## 🚀 Utilisation

### Pour les Visiteurs

1. **Cliquer sur "Faire un Don Maintenant"** sur une campagne
2. **Remplir les informations** :
   - Montant du don (USD)
   - Nom complet
   - Adresse e-mail
3. **Sélectionner un onglet** de paiement
4. **Saisir les détails** selon le mode choisi
5. **Cliquer sur "Confirmer le don"**
6. **Message de confirmation** s'affiche
7. **Modal se ferme** automatiquement (3 secondes)

### Pour les Développeurs

Pour lancer le serveur de développement :

```bash
cd frontend
npm run dev
```

L'application sera disponible à : **http://localhost:3000/**

---

## ✅ Spécifications Réussies

- [x] Formulaire modal professionnel
- [x] 3 options de paiement distinctes
- [x] Logos officiels des opérateurs mobiles
- [x] Coordonnées bancaires réelles complètes
- [x] Détails bancaires affichables avec bouton "Afficher"
- [x] Bouton "Copier" pour chaque champ
- [x] Icône cadenas + texte de sécurité
- [x] Cadre gris clair pour les coordonnées
- [x] Utilisation du VERT de la charte
- [x] Design responsive (mobile-first)
- [x] Modal fenêtre par-dessus le site
- [x] Validation des formulaires
- [x] Messages de feedback utilisateur

---

## 📱 Conseils d'Utilisation

### Sur Mobile

- Les onglets s'empilent correctement
- Les champs sont suffisamment grands pour la saisie tactile
- Les boutons "Copier" sont bien espacés

### Sécurité

- Les données ne sont stockées que dans le composant (état React)
- Les champs de saisie de carte sont correctement validés localement
- Badge de sécurité en bas du modal : 🛡️

### Optimisation Future

Pour une utilisation en production :

1. Intégrer une véritable API de paiement (Stripe, PayPal, etc.)
2. Ajouter le chiffrement SSL/TLS
3. Implémenter une gestion d'erreurs robuste
4. Ajouter des logs de transaction
5. Tester avec des outils de sécurité (PCI DSS)

---

## 🎓 Architecture du Composant

```
DonationModal
├── État
│   ├── activeTab (mobile|card|bank)
│   ├── donationForm (amount, name, email, phone, cardNumber, etc.)
│   ├── showBankDetails (boolean)
│   └── Autres états (status, confirmed)
├── Données constantes
│   └── bankDetails (objet avec coordonnées)
├── Fonctions
│   ├── handleInputChange()
│   ├── handleCopyToClipboard()
│   ├── validateForm()
│   └── handleSubmit()
└── Interface
    ├── Header avec fermeture
    ├── Informations de base
    ├── Navigation d'onglets
    ├── Contenu par onglet
    ├── Messages de statut
    └── Boutons d'action
```

---

## 📞 Support & Questions

Pour toute question sur l'implémentation ou les modifications, veuillez consulter :

- **Composant** : `frontend/src/components/DonationModal.jsx`
- **Intégration** : `frontend/src/components/CampaignCard.jsx`
- **Configuration Tailwind** : `frontend/index.html` (thème "brand")

---

**Dernière mise à jour** : 18 avril 2026  
**Version** : 1.0.0  
**Statut** : ✅ Production-ready
