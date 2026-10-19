# Posemètre 16 — mesure de la lumière et règle du Sunny 16

Application web installable (PWA) pour smartphone, **100 % locale et gratuite** :
pas de serveur, pas de compte. Elle fonctionne **hors ligne** une fois ouverte une première fois.

## Ce que fait l'application

- **Mesure** : « Mesurer la scène » ouvre l'appareil photo du téléphone. L'application lit dans la photo
  les réglages choisis par le téléphone (ouverture, vitesse, ISO) et en déduit l'indice de lumination (IL) de la scène.
  Elle corrige ensuite selon la luminosité réelle de la zone mesurée, ramenée au gris moyen 18 %.
- **Selon la focale** : un cadre rouge montre sur la photo le champ de votre objectif (24, 50, 135 mm…).
  Seule cette zone est mesurée, en mode **Moyenne**, **Pondérée centrale** (comme un reflex) ou **Spot**
  (un toucher sur la photo place le cercle).
- **Résultat** : le couple ouverture / vitesse pour votre film, en mode **Main levée** (vitesse au moins égale
  à 1/focale), **priorité ouverture** ou **priorité vitesse**. Alertes : risque de bougé, pose longue (réciprocité),
  hautes lumières brûlées, sous- ou surexposition, plage de vitesses d'un Pentax LX (1/2000 s à 125 s).
- **Sunny 16** : chaque mesure indique la condition de lumière correspondante et le réglage que donnerait la règle.
  Un onglet permet aussi l'estimation à la main, en lisant l'ombre portée.
- **Boîtier** : film (ISO), focale, ouverture maximale, correction d'exposition. Réglages mémorisés sur le téléphone.
- **Relevés** : historique des mesures enregistrées, sur le téléphone.

### Limites
- Si une photo ne contient pas les réglages d'exposition (capture d'écran, image retouchée), utilisez la
  **saisie manuelle** : recopiez ce qu'affiche le mode Pro de l'appareil photo.
- Le traitement d'image du téléphone peut décaler la mesure : réglez une fois le curseur **Étalonnage**
  en comparant avec une cellule fiable, ou avec le Sunny 16 par soleil franc.

## Utiliser l'application

### Sur ce PC (test)
Lancez le petit serveur fourni, puis ouvrez http://localhost:8080 :

```
powershell -ExecutionPolicy Bypass -File serveur-local.ps1
```

### Sur le smartphone (GitHub Pages)
1. Sur github.com, créez un dépôt **public** (par exemple `posemetre16`).
2. *Add file → Upload files* : déposez **tout le contenu** de ce dossier (pas le dossier lui-même),
   de façon que `index.html` soit à la racine du dépôt. Validez avec *Commit changes*.
3. *Settings → Pages* : *Source* = *Deploy from a branch*, branche `main`, dossier `/ (root)`, *Save*.
4. Après une à deux minutes, l'adresse `https://<vous>.github.io/posemetre16/` est en ligne.

Ouvrez cette adresse sur le téléphone, puis *menu → Ajouter à l'écran d'accueil* (ou *Installer l'application*).

### Mettre à jour
Déposez de nouveau `index.html` dans le dépôt (*Add file → Upload files*). Pour forcer le rafraîchissement
hors ligne, augmentez aussi le numéro de `CACHE` dans `sw.js` (`posemetre16-v2`…).

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | Toute l'application (interface, calculs, lecture EXIF, analyse de l'image) |
| `sw.js`, `manifest.webmanifest`, `icons/` | Installation et fonctionnement hors ligne |
| `serveur-local.ps1` | Serveur de test sur le PC |
