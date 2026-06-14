# Carte d'identité numérique
**Houedannou Giannuzzi Midokpe**

Fichier : `carte_numerique_houedannou.html`
Version : 1.0 — Single-file, no-scroll, no-dependency

---

## Présentation

Page web statique servant de carte de visite numérique. Conçue dans un esprit minimaliste éditorial : une seule surface, aucun scroll, tout visible d'un coup d'œil. Zéro framework, zéro bibliothèque JavaScript, un seul fichier HTML autonome.

---

## Structure de la page

```
card (100dvh, flex colonne)
│
├── header.top          — label discret en haut
├── main.center         — le nom, point focal unique
│     ├── h1 (.n-row × 3)   — Houedannou / Giannuzzi / Midokpe
│     └── .subtitle     — Cheffe d'entreprise · Toulouse — Cotonou
│
└── footer.bottom
      ├── .meta         — activités (gauche) + coordonnées (droite)
      └── nav.cta       — 4 boutons d'action
            ├── WhatsApp
            ├── Appeler
            ├── E-mail
            └── Quitter
```

---

## Typographie

| Usage | Famille | Style | Graisse |
|---|---|---|---|
| Nom | Cormorant Garamond | Normal | 300 |
| Rôle | Cormorant Garamond | Italique | 300 |
| Labels, boutons | Josefin Sans | Normal | 300 / 400 / 600 |

Source : Google Fonts (chargé via `<link>` en tête de fichier).

---

## Palette

| Token CSS | Valeur | Usage |
|---|---|---|
| `--bg` | `#161412` | Fond unique |
| `--fg` | `#f2efe9` | Texte principal, boutons |
| `--gold` | `#b9965f` | Rôle italique, accent doré |
| `--muted` | `#807a70` | Labels secondaires, lieux |
| `--hair` | `rgba(242,239,233,.12)` | Filets séparateurs, grille boutons |

---

## Animations

Toutes les animations sont en CSS pur, sans JavaScript.

| Élément | Animation | Délai |
|---|---|---|
| Label haut | `fade` 0.8s | 0.1s |
| Ligne 1 du nom | `rise` 1s spring | 0.2s |
| Ligne 2 du nom | `rise` 1s spring | 0.32s |
| Ligne 3 du nom | `rise` 1s spring | 0.44s |
| Sous-titre | `fade` 0.8s | 0.9s |
| Bloc meta | `fade` 0.8s | 1.1s |
| Grille boutons | `fade` 0.8s | 1.25s |

`prefers-reduced-motion` : toutes les animations sont neutralisées si l'utilisateur a activé la réduction de mouvement dans son système.

---

## Boutons d'action

| Bouton | Action |
|---|---|
| WhatsApp | `https://wa.me/33623456789` — ouvre WhatsApp |
| Appeler | `tel:+33623456789` — compose le numéro |
| E-mail | `mailto:desireeladuchesse@gmail.com` — ouvre le client mail |
| Quitter | `window.close()` — ferme l'onglet |

> **Note sur le bouton Quitter** : `window.close()` n'est autorisé par les navigateurs que sur les onglets ouverts programmatiquement (via `window.open`). Sur un onglet ouvert directement par l'utilisateur, certains navigateurs ignorent l'appel — comportement de sécurité standard, non contournable en front-end.

Comportement hover : fond blanc / texte noir (inversion), transition 0.3s. Sur mobile `(:active)` : opacité 0.8.

---

## Responsive & No-Scroll

La contrainte no-scroll est garantie par trois mécanismes :

```css
/* 1. dvh : tient compte de la barre du navigateur mobile */
height: 100dvh;

/* 2. safe-area : respect des encoches iPhone / Android */
padding-top: max(env(safe-area-inset-top), clamp(28px, 5vh, 64px));
padding-bottom: max(env(safe-area-inset-bottom), clamp(24px, 4vh, 56px));

/* 3. flex compressible : la section nom cède de l'espace en cas de hauteur réduite */
.center { flex: 1; min-height: 0; }
```

### Breakpoints

| Contexte | Comportement |
|---|---|
| Mobile `≤ 540px` | Labels boutons masqués (icônes seules), coordonnées empilées |
| Paysage bas `h ≤ 460px` | Nom réduit, bloc meta masqué pour préserver les boutons |
| Desktop | Layout complet, marges fluides via `clamp()` |

---

## Personnalisation

### Changer les coordonnées

Toutes les infos sont dans `<footer class="bottom">` :

```html
<!-- Numéro WhatsApp (format international, sans +) -->
<a href="https://wa.me/33623456789">

<!-- Numéro d'appel -->
<a href="tel:+33623456789">

<!-- E-mail -->
<a href="mailto:desireeladuchesse@gmail.com">

<!-- Bloc texte visible -->
<b>06 23 45 67 89</b>
desireeladuchesse@gmail.com
12 rue Blaise Pascal, 33000 Bordeaux
```

### Changer la couleur d'accent

Modifier la variable `--gold` dans `:root` :

```css
:root {
  --gold: #b9965f; /* → remplacer par la couleur souhaitée */
}
```

### Changer les polices

Remplacer les `@import` Google Fonts en tête de fichier et mettre à jour les références `font-family` dans le CSS.

---

## Déploiement

Le fichier est **entièrement autonome** — aucune dépendance locale. Il suffit de :

- L'héberger sur n'importe quel serveur statique (GitHub Pages, Netlify, Vercel, OVH, etc.)
- Ou l'envoyer directement par e-mail / WhatsApp pour ouverture dans un navigateur

Aucun build, aucune compilation, aucune base de données.

---

## Compatibilité

| Navigateur | Support |
|---|---|
| Chrome / Edge 90+ | ✅ Complet |
| Safari iOS 15+ | ✅ Complet (dvh, safe-area) |
| Firefox 110+ | ✅ Complet |
| Samsung Internet 16+ | ✅ Complet |
| IE 11 | ✗ Non supporté |

---

*Conçu et développé avec Claude — Anthropic, 2026.*
