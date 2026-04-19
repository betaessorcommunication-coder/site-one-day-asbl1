# Checklist de Validation - Tunnel de Don

## Test d'Acceptation - 18 avril 2026

---

## 📋 Prérequis

- [ ] Serveur Vite lancé : `npm run dev` (port 3000)
- [ ] Navigateur web ouvert : http://localhost:3000/
- [ ] Console DevTools ouverte pour vérifier les erreurs

---

## 1️⃣ Accès au Formulaire de Don

### Première Action

- [ ] Naviguer jusqu'à la section "Nos Campagnes Actives"
- [ ] Voir au moins une carte de campagne s'afficher
- [ ] Bouton "💚 Faire un Don Maintenant" est visible sur chaque campagne

### Au Clic

- [ ] Modal s'ouvre par-dessus le contenu
- [ ] Modal ne quitte pas la page (navigation conservée)
- [ ] Fermeture possible via bouton "✕" en haut à droite

---

## 2️⃣ Interface de Base

### Header du Modal

- [ ] Icône cadenas 🔒 affichée
- [ ] Texte "Paiement 100% sécurisé" visible
- [ ] Titre "Soutenir [Nom Campagne]"
- [ ] Description visible

### Formulaire d'Information

- [ ] Champ "Montant du don (USD)" présent
- [ ] Champ "Votre nom complet" présent
- [ ] Champ "Adresse e-mail" présent
- [ ] Tous les champs marqués avec astérisque "\*"

### Onglets de Paiement

- [ ] 3 onglets visibles : "📱 Mobile Money", "💳 Carte Bancaire", "🏦 Virement"
- [ ] Onglet actif : couleur VERT (brand-600)
- [ ] Onglets inactifs : couleur grise
- [ ] Clic sur onglet change l'affichage

---

## 3️⃣ Option A : Mobile Money (RDC)

### Contenu

- [ ] Texte d'instruction visible
- [ ] 3 cartes d'opérateurs s'affichent : M-Pesa, Orange Money, Airtel Money
- [ ] Logos officiels visibles pour chaque opérateur
- [ ] Champ "Numéro de téléphone" présent
- [ ] Placeholder : "+243 812 345 678"

### Interaction

- [ ] Clic sur opérateur sélectionne la radio
- [ ] Sélection visuelle change (border, highlight)
- [ ] Numéro de téléphone peut être saisi

---

## 4️⃣ Option B : Carte Bancaire

### Contenu

- [ ] 2 cartes de types de carte : Visa, Mastercard
- [ ] Logos officiels visibles
- [ ] Champ "Numéro de carte" : placeholder "1234 5678 9012 3456"
- [ ] Champ "Date d'expiration" : placeholder "MM/YY"
- [ ] Champ "CVV" : placeholder "123"

### Restrictions

- [ ] Numéro de carte limité à 19 caractères
- [ ] Date expiration limitée à 5 caractères
- [ ] CVV limité à 4 caractères

### Interaction

- [ ] Sélection du type de carte fonctionne
- [ ] Saisie des champs disponible

---

## 5️⃣ Option C : Virement Bancaire

### État Initial

- [ ] Bouton "Afficher les coordonnées bancaires" visible
- [ ] Bouton a icône 🔓
- [ ] Arrière-plan vert (brand-600)
- [ ] Texte blanc

### Au Clic du Bouton

- [ ] Bouton disparaît
- [ ] 7 cartes d'informations s'affichent

### Détails Bancaires (7 adrficards)

- [ ] **Card 1** - Bénéficiaire : "Christian Kabamba Ebondo"
- [ ] **Card 2** - IBAN : "BE34 6505 6439 1190"
- [ ] **Card 3** - BIC : "REVOBEB2"
- [ ] **Card 4** - Banque Correspondante : "CHASDEFX"
- [ ] **Card 5** - Compte Institutionnel : "One Day ASBL"
- [ ] **Card 6** - Banque : "Trust Merchant Bank S.A (TMB)"
- [ ] **Card 7** - Numéro de Compte : "00017-11020-7305157000-03"

### Boutons Copier

- [ ] Chaque card a un bouton "Copier"
- [ ] Bouton blanc/gris initialement
- [ ] Au clic : bouton devient vert
- [ ] Texte change en "✓ Copié"
- [ ] Texte revient après 2 secondes
- [ ] Contenu est copié au presse-papiers

---

## 6️⃣ Validation du Formulaire

### Test d'Envoi Vide

- [ ] Clic sur "Confirmer le don" sans remplir
- [ ] Message d'erreur : "Veuillez remplir tous les champs obligatoires."
- [ ] Modal reste ouvert

### Test avec Données Incomplètes

- [ ] Remplir "Montant" et "Nom" uniquement
- [ ] Clic sur "Confirmer le don"
- [ ] Message d'erreur approprié

### Test avec Données Valides - Mobile Money

- [ ] Montant : "50"
- [ ] Nom : "Jean Dupont"
- [ ] Email : "jean@exemple.com"
- [ ] Sélectionner onglet "Mobile Money"
- [ ] Sélectionner M-Pesa
- [ ] Numéro : "+243 812 345 678"
- [ ] Clic sur "Confirmer le don"
- [ ] Message de confirmation s'affiche
- [ ] Message inclut le montant et le nom
- [ ] Icône ✓ affichée
- [ ] modal se ferme après 3 secondes

---

## 7️⃣ Design & UX

### Couleurs

- [ ] Couleur verte (brand-600 : #059669) utilisée pour boutons actifs
- [ ] Couleur plus foncée (brand-700 : #047857) au hover
- [ ] Arrière-plans gris clair (#f9fafb)
- [ ] Cohérence avec le reste du site

### Responsive

**Sur Desktop (1024px+)** :

- [ ] Modal centré
- [ ] Largeur max 896px
- [ ] Bien espacé

**Sur Tablette (768px - 1023px)** :

- [ ] Modal adapté
- [ ] Onglets côte à côte
- [ ] Buttons lisibles

**Sur Mobile (375px - 767px)** :

- [ ] Modal remplit l'écran avec padding
- [ ] Onglets bien espacés
- [ ] Texte lisible (16px+)
- [ ] Boutons assez grands pour le tactile
- [ ] Pas de débordement horizontal

### Accessibilité

- [ ] Focus visible sur les boutons (avec clavier Tab)
- [ ] Tous les labels sont associés aux inputs
- [ ] Icônes seules ont du texte alt ou aria-label
- [ ] Contraste des couleurs acceptable

---

## 8️⃣ Fermeture du Modal

### Via Bouton Annuler

- [ ] Clic sur "Annuler"
- [ ] Modal se ferme
- [ ] État réinitialisé

### Via Bouton ✕

- [ ] Clic sur ✕
- [ ] Modal se ferme
- [ ] État réinitialisé

### Via Confirmation

- [ ] Après "Confirmer le don" avec données valides
- [ ] Message de confirmation s'affiche 3 secondes
- [ ] Modal se ferme automatiquement
- [ ] Page est intacte (pas de recharge)

---

## 9️⃣ Tests Avancés

### Copie au Presse-Papiers (Mobile Money)

- [ ] Saisir un numéro de téléphone
- [ ] Copier dans un autre onglet/application
- [ ] Vérifier le contenu pour vérification

### Multiple Soumissions

- [ ] Ouvrir modal → Remplir → Confirmer
- [ ] Modal se ferme
- [ ] Rouvrir modal
- [ ] État réinitialisé (champs vides)

### Navigation d'Onglets Rapide

- [ ] Cliquer rapidement entre les onglets
- [ ] Pas de bugs visuels
- [ ] Affichage correct

---

## 🔟 Erreurs Console

### À Vérifier

Dans DevTools (F12) → Console

- [ ] Aucun erreur rouge
- [ ] Aucun warning critique
- [ ] Aucun erreur 404 sur images

### Logos

- [ ] Images M-Pesa, Orange, Airtel charges correctement
- [ ] Logos Visa/Mastercard se chargent
- [ ] Fallback si image échoue (graceful degradation)

---

## 📝 Résumé de la Validation

| Composant             | Statut | Remarques |
| --------------------- | ------ | --------- |
| DonationModal.jsx     | ✅/❌  |           |
| CampaignCard.jsx      | ✅/❌  |           |
| Responsive Desktop    | ✅/❌  |           |
| Responsive Mobile     | ✅/❌  |           |
| Mobile Money          | ✅/❌  |           |
| Carte Bancaire        | ✅/❌  |           |
| Virement Bancaire     | ✅/❌  |           |
| Coordonnées Bancaires | ✅/❌  |           |
| Boutons Copier        | ✅/❌  |           |
| Validation            | ✅/❌  |           |
| Aucune erreur console | ✅/❌  |           |

---

## 🚀 Prochaines Étapes (Optionnelles)

- [ ] Intégration API de paiement réelle (Stripe, PayPal, etc.)
- [ ] Tests de sécurité (PCI DSS)
- [ ] Tests A/B avec des utilisateurs réels
- [ ] Monitoring d'erreurs (Sentry, LogRocket)
- [ ] Analytics des donations (Google Analytics)
- [ ] Confirmation par email automatique
- [ ] Historique des donations (Dashboard)

---

**Dernière vérification** : ****\_\_****  
**Testé par** : ****\_\_****  
**Résultat Global** : ✅ VALIDÉ / ❌ À CORRIGER

---

## 📞 Notes & Observations

```
[Espace pour les notes de test]
_____________________________________________________________________________

_____________________________________________________________________________

_____________________________________________________________________________
```
