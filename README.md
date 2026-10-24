# README - SAVORA

## Présentation

SAVORA est un site web de restauration multipage développé en HTML5, CSS3 et JavaScript natif. Il permet aux clients de consulter le menu, de gérer un panier, de préparer une commande et une demande de réservation, le tout transmis par WhatsApp.

**Nom de marque:** SAVORA  
**Slogan:** Toutes les saveurs, une seule adresse.

## Pages du site

Le site comprend 7 pages principales :

- `index.html` - Page d'accueil
- `menu.html` - Menu interactif avec recherche et filtrage
- `panier.html` - Gestion du panier
- `commande.html` - Formulaire de commande et transmission WhatsApp
- `reservation.html` - Demande de réservation par WhatsApp
- `apropos.html` - Présentation de SAVORA
- `contact.html` - Informations de contact

## Structure des dossiers

```
KMC/
├── index.html
├── menu.html
├── panier.html
├── commande.html
├── reservation.html
├── apropos.html
├── contact.html
├── style.css
├── README.md
├── assets/          # Images originales
├── img/             # Images copiées/utilisées
├── js/
│   ├── config.js    # Configuration WhatsApp
│   ├── products.js  # Données des produits
│   ├── cart.js      # Logique du panier (localStorage)
│   ├── menu.js      # Affichage du menu
│   ├── cart-page.js # Affichage du panier
│   ├── checkout.js  # Formulaire de commande
│   ├── reservation.js # Formulaire de réservation
│   ├── contact.js   # Gestion du formulaire contact
│   └── main.js      # Menu hamburger et fonctions communes
└── docs/
    └── CAHIER_DES_CHARGES.md
```

## Ouvrir et tester le site

1. Ouvrir le dossier du projet
2. Ouvrir `index.html` directement dans un navigateur web (pas besoin de serveur local)
3. Le site fonctionne en mode statique

## Fonctionnement du panier

- Le panier est sauvegardé dans `localStorage` avec la clé `savora_cart`
- Ajout, modification de quantité, suppression d'articles
- Calcul automatique des totaux
- Persistance après rechargement de la page
- Gestion des paniers vides et données corrompues

## Configuration du numéro WhatsApp officiel

**IMPORTANT:** Le site est livré avec un numéro de configuration placeholder.

1. Ouvrir `js/config.js`
2. Remplacer `NUMERO_A_CONFIGURER` par le numéro WhatsApp officiel du restaurant
3. Le format doit être sans `+` ni `00`, uniquement des chiffres (ex: `225XXXXXXXXX`)
4. Sauvegarder le fichier

Tant que le numéro n'est pas configuré, un message d'alerte s'affichera lors de la tentative d'envoi.

## Comment les commandes sont préparées

1. L'utilisateur ajoute des produits au panier
2. Il va sur `commande.html` et remplit le formulaire
3. Le site vérifie le panier, les champs obligatoires et l'adresse si livraison
4. Un message structuré est construit avec tous les détails
5. Le message est encodé avec `encodeURIComponent()`
6. WhatsApp s'ouvre avec l'URL `wa.me/NUMERO?text=...`

**Le client doit lui-même vérifier et envoyer le message dans WhatsApp. Le site n'envoie rien automatiquement.**

## Comment les réservations sont préparées

1. L'utilisateur remplit le formulaire sur `reservation.html`
2. Le site valide les champs (nom, téléphone, date, heure, nombre de personnes)
3. Les dates passées sont refusées
4. Un message structuré est construit
5. WhatsApp s'ouvre avec la demande préparée

**La réservation n'est pas confirmée automatiquement. Le restaurant doit vérifier les disponibilités et répondre.**

## Actions requises du client dans WhatsApp

- **Commandes:** Ouvrir WhatsApp → Vérifier le message → Appuyer sur "Envoyer"
- **Réservations:** Ouvrir WhatsApp → Vérifier le message → Appuyer sur "Envoyer"

## Limitations (absence de backend)

- Pas de confirmation automatique des commandes ou réservations
- Pas de paiement en ligne
- Pas d'espace administrateur
- Pas de base de données
- Le panier est uniquement côté navigateur
- Le formulaire de contact n'envoie pas réellement d'e-mails
- Les disponibilités ne sont pas vérifiées automatiquement

## Évolutions possibles

- Ajout d'un backend (Node.js, PHP, etc.)
- Base de données pour les commandes
- Espace administrateur
- Système de paiement en ligne
- Gestion des disponibilités
- Notifications automatiques
- Historique des commandes

## Technologies utilisées

- HTML5
- CSS3
- JavaScript natif
- localStorage
- Liens WhatsApp wa.me
- Font Awesome (icônes)

## Palette de couleurs

- Bordeaux principal: `#7b1b2e`
- Bordeaux foncé: `#5e1522`
- Vert sauge: `#9cb270`
- Blanc: `#ffffff`
- Bleu nuit: `#1a1a2e`
