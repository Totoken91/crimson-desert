# DÉSERT CRAMOISI — Brief prototype point & click
## Document destiné à Claude Code pour implémentation

---

## Contexte du projet

Jeu d'horreur narratif point & click, expérience web interactive. Pas de moteur de jeu — tourne entièrement dans le navigateur. Stack : HTML + CSS + JS vanilla. Déployable sur Vercel ou itch.io.

Le joueur incarne une anomalie qui explore un désert cramoisi sans comprendre ce qu'il est. La narration révèle progressivement son identité à travers des fragments cryptiques. Il dispose d'un système d'alchimie rituelle pour progresser — chaque craft a un coût permanent sur lui-même et sur le rendu visuel du jeu.

---

## Ce que Claude Code doit produire

Un prototype jouable en HTML/CSS/JS vanilla contenant :

1. **Une scène complète** avec photo placeholder traitée (simuler la photo avec un canvas généré)
2. **Système de point & click** — zones cliquables invisibles sur la scène, fragments narratifs au clic
3. **Interface complète** — boîte de dialogue, portrait, inventaire ressources, point d'alchimie
4. **Système de ressources** — collecter Douleur / Essence / Matière organique
5. **4 recettes alchimiques** Tier I fonctionnelles
6. **Effets visuels CSS** — scanlines, grain, vignette, dégradation progressive
7. **Architecture modulaire** prête à recevoir les vraies photos et les scènes suivantes

---

## Architecture des fichiers

```
desert-cramoisi/
├── index.html
├── style.css
├── main.js
├── engine/
│   ├── scene.js       ← gestion des scènes et transitions
│   ├── inventory.js   ← ressources + alchimie
│   ├── narrative.js   ← fragments de texte + typage
│   └── state.js       ← état global du jeu (persisté en localStorage)
├── scenes/
│   └── scene-01.js    ← données de la scène 01 (hotspots, textes, ressources)
└── assets/
    └── (photos traitées viendront ici — PNG ou JPG)
```

---

## Esthétique & palette

**Palette principale (CSS variables à définir) :**
```css
--bg:        #080506;   /* noir profond */
--bg2:       #100b0a;   /* surface */
--bg3:       #160e0c;   /* surface hover */
--crimson:   #8C1C1C;   /* rouge sang */
--crimson-l: #BE372D;   /* rouge rituel */
--rust:      #6B2416;   /* rouille */
--bone:      #C6B29B;   /* os */
--bone-dim:  #8A7A6A;   /* os atténué */
--ash:       #3A3230;   /* cendre */
--ash-l:     #5A4E4A;   /* cendre clair */
--pale:      #E8DDD0;   /* blanc cassé */
--purple:    #3E2848;   /* magie */
--purple-l:  #7A4FA0;   /* magie clair */
```

**Typographie :**
- `'Cinzel'` (Google Fonts) — titres, noms rituels
- `'Crimson Pro'` (Google Fonts) — texte narratif, corps
- `'JetBrains Mono'` (Google Fonts) — labels UI, codes, tags

**Effets visuels obligatoires (CSS/JS) :**
- Grain animé sur `body::before` (SVG fractalNoise, opacity ~0.6)
- Scanlines via `repeating-linear-gradient` en position `fixed`, pointer-events none
- Vignette radiale autour de la scène
- Variable `--pain-level` (0.0 à 1.0) qui pilote dynamiquement : intensité vignette, saturation image, distorsion

---

## Structure HTML de l'interface de jeu

```
#game-shell
  #scene-container          ← photo plein écran ou canvas placeholder
    #scene-image            ← <img> ou <canvas>
    #hotspot-layer          ← <svg> superposé, zones cliquables
    #drawing-layer          ← <canvas> pour les dessins par-dessus (vide pour l'instant)
    #fx-layer               ← scanlines + grain (pointer-events: none)
    #cursor-custom          ← curseur contextuel SVG (oeil / main / flamme)
  
  #dialog-box               ← boîte de dialogue en bas
    #dialog-portrait        ← <canvas> 48×48, portrait pixel art généré
    #dialog-speaker         ← "anomalie" en JetBrains Mono
    #dialog-text            ← texte qui se tape caractère par caractère
    #dialog-continue        ← triangle animé (apparaît quand le texte est fini)
  
  #hud                      ← UI en haut
    #resource-bar           ← affichage des 3 ressources
    #eye-btn                ← bouton œil en haut à droite (révèle les hotspots)
  
  #alchemy-panel            ← panneau qui s'ouvre sur un point d'alchimie
    (recettes disponibles selon ressources possédées)
  
  #nav-zones                ← zones de navigation scène (bords cliquables ou icônes)
```

---

## Système de scènes

Chaque scène est un objet JS :

```javascript
// scenes/scene-01.js
export const scene01 = {
  id: 'scene-01',
  label: 'Les Dunes plates',
  intro: "Tu étais là avant que le sable existe.",
  bgImage: null, // null = canvas généré ; string = chemin vers la photo
  bgGenerator: 'dunes', // si bgImage null, quel générateur canvas utiliser
  
  hotspots: [
    {
      id: 'hs-01',
      label: 'cercle de cendre',
      // coordonnées en % pour être responsive
      x: 38, y: 62, w: 16, h: 10,
      shape: 'ellipse', // 'rect' | 'ellipse' | 'poly'
      cursor: 'eye',
      resource: { type: 'essence', amount: 1 },
      texts: [
        "Le cercle a été tracé avec quelque chose qui brûlait encore.",
        "Tu reconnais le tracé. Tu n'as jamais appris à tracer.",
      ],
      // collectible : si true, disparaît après interaction + donne la ressource
      collectible: true,
    },
    {
      id: 'hs-02',
      label: 'horizon',
      x: 0, y: 30, w: 100, h: 20,
      shape: 'rect',
      cursor: 'eye',
      resource: null,
      texts: [
        "L'horizon devrait être là. Il y est. Mais pas pour toi.",
        "Tu n'as pas de direction. Tu as une présence.",
      ],
      collectible: false,
    },
    {
      id: 'hs-alchimie',
      label: 'point d\'alchimie',
      x: 45, y: 70, w: 10, h: 15,
      shape: 'ellipse',
      cursor: 'flame',
      resource: null,
      texts: [],
      // type spécial : ouvre le panneau d'alchimie
      action: 'open-alchemy',
      collectible: false,
    }
  ],
  
  // zones de navigation vers d'autres scènes
  exits: [
    { direction: 'right', targetScene: 'scene-02', x: 88, y: 20, w: 12, h: 80, locked: true, lockedText: "Quelque chose bloque ce passage. Un craft spécifique peut l'ouvrir." }
  ],
  
  // Scène débloquée si ce craft a été accompli
  unlockCondition: null,
}
```

---

## Système de ressources

3 types de ressources, stockées dans l'état global :

```javascript
state.inventory = {
  douleur:  0,   // rouge — D
  essence:  0,   // violet — S
  organique: 0,  // ambre — O
}
```

Affichage dans la HUD :
- Icône + compteur pour chaque ressource
- Police JetBrains Mono, couleurs distinctes (rouge / violet / ambre)
- Animation +1 flottant quand une ressource est ramassée

---

## Système d'alchimie

```javascript
// Données des recettes — à mettre dans engine/inventory.js
export const RECIPES = [
  {
    id: 'lanterne-os',
    name: 'Lanterne d\'os',
    tier: 1,
    cost: { douleur: 2, essence: 1, organique: 1 },
    effect: "Révèle les zones cliquables cachées pendant 3 inspections.",
    ritualCost: "Une douleur sourde dans les mains. Permanente.",
    // Effet mécanique
    mechanic: 'reveal-hotspots',
    // Effet visuel permanent sur le joueur (modifie --pain-level)
    painDelta: 0.05,
  },
  {
    id: 'tuile-memoire',
    name: 'Tuile de mémoire',
    tier: 1,
    cost: { douleur: 3, essence: 2, organique: 0 },
    effect: "Fragment de mémoire gravé dans le sable. Débloque la narration de la scène suivante.",
    ritualCost: "Le nom de quelque chose disparaît. Tu ne sais pas quoi.",
    mechanic: 'unlock-narrative',
    painDelta: 0.08,
  },
  {
    id: 'armure-peau',
    name: 'Armure de peau',
    tier: 1,
    cost: { douleur: 0, essence: 1, organique: 1 },
    effect: "Absorbe une fraction de la douleur des prochains crafts.",
    ritualCost: "Le souvenir du visage de la créature te hante pendant 3 cycles.",
    mechanic: 'pain-absorb',
    painDelta: 0.03,
  },
  {
    id: 'lien-nerf',
    name: 'Lien de nerf',
    tier: 1,
    cost: { douleur: 3, essence: 0, organique: 2 },
    effect: "Lie deux éléments du monde. Débloque un passage verrouillé.",
    ritualCost: "Mobilité réduite de 20% de façon permanente après chaque utilisation.",
    mechanic: 'unlock-exit',
    painDelta: 0.1,
  },
]
```

**Logique du panneau d'alchimie :**
- S'ouvre uniquement si le joueur est sur un hotspot `action: 'open-alchemy'`
- Affiche les recettes avec leurs coûts — grisées si ressources insuffisantes
- Bouton craft → animation rituelle (2s, distorsion canvas) → application effets
- `painDelta` s'accumule dans `state.painLevel` → pilote les effets visuels

---

## Système de narration (typage de texte)

```javascript
// engine/narrative.js
// typeText(text, targetElement, speed, onComplete)
// Tape le texte caractère par caractère
// Affiche le triangle "continuer" quand c'est fini
// Clic sur la boîte ou appui espace → skip / passer au texte suivant
```

Comportement :
- Vitesse : 22ms par caractère
- Clic pendant le typage → affiche le texte en entier immédiatement
- Clic quand texte complet → ferme la boîte ou passe au fragment suivant
- Le portrait (canvas 48×48) affiche une forme pixel art abstraite — pas un visage humain

---

## État global & persistance

```javascript
// engine/state.js
const defaultState = {
  currentScene: 'scene-01',
  inventory: { douleur: 0, essence: 0, organique: 0 },
  painLevel: 0.0,          // 0.0 → 1.0, augmente à chaque craft
  crafted: [],             // IDs des crafts accomplis
  inspected: {},           // { [sceneId]: [hotspotId, ...] }
  exits: {},               // { [exitId]: true } exits débloqués
  narrativeFlags: {},      // flags narratifs déclenchés
  endingScore: {           // tracking silencieux pour les fins
    sacrifice: 0,          // prélèvements sur les entités
    selfHarm: 0,           // prélèvements sur soi
    memory: 0,             // fragments de mémoire utilisés
  },
}

// Persister dans localStorage, charger au démarrage
// Exposer : getState(), setState(patch), resetState()
```

---

## Effets visuels progressifs selon painLevel

`painLevel` va de 0 à 1 et s'accumule à chaque craft. Il pilote dynamiquement :

```css
/* À mettre à jour via JS : document.documentElement.style.setProperty('--pain', value) */

/* Vignette — s'intensifie */
--vignette-size: calc(60% + var(--pain) * 40%);
--vignette-opacity: calc(0.4 + var(--pain) * 0.6);

/* Saturation image — se désature */
filter: saturate(calc(1 - var(--pain) * 0.7)) contrast(calc(1 + var(--pain) * 0.3));

/* Distorsion — à partir de 0.6 */
/* Activer via canvas WebGL ou CSS filter blur/displacement au-delà d'un seuil */

/* Grain — s'intensifie */
/* Modifier l'opacité du layer grain */
```

À `painLevel >= 0.8` : la boîte de dialogue commence à afficher des caractères corrompus (substitution aléatoire de glyphes).

---

## Curseur contextuel

3 états selon le hotspot survolé :
- `eye` — inspection / lecture (SVG : oeil ouvert)
- `hand` — collecte de ressource (SVG : main squelettique simplifiée)
- `flame` — point d'alchimie (SVG : flamme simple)
- `default` — curseur normal (CSS custom : croix fine cramoisie)

Implémenter via un `<div id="cursor-custom">` qui suit la souris et change de contenu SVG selon le contexte.

---

## Canvas placeholder (en l'absence de vraies photos)

Pour la scène 01, générer un fond procédural canvas qui simule l'ambiance :

```javascript
// Teintes : noir #080506, rouge sombre #2A0A08, cramoisie #8C1C1C
// Technique : dégradés radiaux superposés + grain canvas + quelques lignes d'horizon
// Pas besoin d'être beau — juste assez pour tester le système
function drawDunes(canvas) {
  // fond noir
  // quelques plans de dunes en rouges sombres
  // grain lourd via getImageData + noise
  // lumière froide sur un bord (simuler une lune ou une source mystique)
}
```

Prévoir un système de swap simple : si `bgImage` est défini dans la scène, utiliser `<img>` à la place du canvas. Les hotspots fonctionnent dans les deux cas (coordonnées en %).

---

## Ce qui N'est PAS dans le prototype (phase 2+)

- Entités animées (fantômes, gardiens d'os)
- Recettes Tier II et Tier III
- Système de fins complet
- Son et musique
- Scènes 02, 03, et scène verrouillée ██
- Altérations visuelles complexes (WebGL)
- La vraie photo de jardin de nuit et le cerf surexposé (fournis plus tard)

---

## Comportements importants à implémenter correctement

1. **Les hotspots ne sont pas visibles par défaut** — seulement au survol (cursor change) ou si le craft Lanterne d'os est actif
2. **Le bouton œil** (haut droite) révèle temporairement tous les hotspots avec un contour dim
3. **Chaque texte d'inspection a 2 variantes** — alterner aléatoirement entre les deux
4. **Un hotspot collectible** disparaît après collecte (retirer du SVG layer) et ne revient pas
5. **La boîte de dialogue** est fermée par défaut — s'ouvre uniquement sur interaction
6. **Le panneau alchimie** est une modale overlay sombre, pas une page séparée
7. **L'état est persisté** — si le joueur recharge, il retrouve son avancement (localStorage)
8. **Pas de barre de progression, pas de score affiché** — tout est silencieux et non-verbalisé

---

## Livrable attendu

Un dossier `desert-cramoisi/` avec tous les fichiers listés dans l'architecture, fonctionnel en ouvrant `index.html` dans un navigateur (pas de serveur requis pour le prototype — si modules ES nécessaires, prévoir un `vite` ou bundler minimal, ou tout mettre en IIFE vanilla).

La phase 0 est validée quand : on peut cliquer dans la scène, ramasser des ressources, ouvrir le panneau alchimie, crafter une recette Tier I, et voir le `painLevel` affecter le rendu visuel.
