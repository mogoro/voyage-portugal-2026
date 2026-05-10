# Grand Tour Ibérique 2026 — Carnet de voyage

Carnet de voyage **PWA installable** pour le road-trip famille Mogoro,
été 2026 (France · Espagne · Portugal · 21 jours).

## Installer comme application

- **Android Chrome / Edge** : ouvrir le site, menu **⋮ → Installer l'application** (ou bannière proposée).
- **iOS Safari** : bouton **Partager → Sur l'écran d'accueil**.
- **Desktop (Chrome/Edge)** : icône **+** à droite de la barre d'adresse → **Installer**.

L'app s'ouvre alors comme une vraie application, plein écran, avec icône
sur l'écran d'accueil. Fonctionne hors-ligne pour le contenu déjà visité
(les tuiles de carte nécessitent un réseau).

## Ouvrir en mode dev

Double-clic sur `index.html` — le site fonctionne en local sauf le
service worker (qui requiert HTTPS ou `localhost`).

Pour tester la PWA en local :

```powershell
# avec Python (si installé)
python -m http.server 8080
# puis http://localhost:8080
```

## Structure

- `index.html` — l'app complète (CSS + JS inline)
- `manifest.webmanifest` — manifeste PWA
- `sw.js` — service worker (cache-first sur le shell)
- `icon.svg` / `icon-maskable.svg` — icônes (vectorielles, scalables)
- `images/` — dossier pour les photos personnelles
- `.gitignore`

## Ajouter des photos

1. Dépose tes JPG dans `images/`
2. Nomme-les selon les slugs attendus :
   - `bordeaux-1.jpg`, `bordeaux-2.jpg`, `bordeaux-3.jpg`
   - `hondarribia-1.jpg` à `hondarribia-4.jpg`
   - `cantabrie-1.jpg` à `cantabrie-4.jpg`
   - `picos-1.jpg` à `picos-4.jpg`
   - `lugo-1.jpg` à `lugo-3.jpg`
   - `porto-1.jpg` à `porto-6.jpg`
   - `guimaraes-1.jpg` à `guimaraes-4.jpg`
   - `lisbonne-1.jpg` à `lisbonne-8.jpg`
   - `salamanque-1.jpg` à `salamanque-3.jpg`
3. Recharge la page

Format conseillé : 1200 × 900 px, JPG optimisé < 200 ko.

## Mise à jour du contenu

- **Hébergements** : remplacer `class="todo">à compléter` par les
  vraies infos dans `index.html`, onglet *Hébergements*.
- **Bump de version** PWA : après modification, incrémenter `CACHE_NAME`
  dans `sw.js` (ex. `voyage-iberique-2026-v2`) pour forcer le rechargement
  côté client.

## Déploiement GitHub Pages

Le repo est hébergé sur GitHub (compte perso `mogoro`).
Pour activer Pages :

1. Settings → Pages → Source : `Deploy from a branch`
2. Branch : `main` / dossier : `/ (root)`
3. URL : `https://mogoro.github.io/voyage-portugal-2026/`

## Onglets

1. **Vue d'ensemble** — stats + résumé
2. **Carte** — itinéraire Leaflet interactif
3. **Jour par jour** — timeline 21 jours
4. **Hébergements** — fiches détaillées + suggestions
5. **Budget** — 3 scénarios
6. **Recharge VE** — apps, étapes tendues
7. **Visites** — sélection par ville
8. **Photos** — galerie (placeholders à remplacer)
9. **Pratique** — documents, urgences, bagages

## Dépendances externes (CDN)

- Google Fonts (Cormorant Garamond + Inter)
- Leaflet 1.9.4 (CSS + JS)
- OpenStreetMap tiles
