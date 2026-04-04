# ANOMALIE — jeu d'horreur narratif

> *Tu existais avant qu'ils posent le parquet.*

Projet collaboratif Kenny + Alexandra. Jeu d'horreur narratif point & click, expérience web interactive.

---

## Concept

Le joueur incarne une anomalie qui habite un espace domestique — sans s'en rendre compte. Inspiré de l'ambiance de *I Live Under Your House* : ton surréaliste, images dégradées, narration cryptique. Le joueur comprend ce qu'il est avant le personnage. C'est ça le malaise.

Pas de monstre. Pas d'explication. Juste la présence.

---

## Esthétique

- Palette EGA vert acide / noir — référence directe aux screenshots *ILUYH*
- Photos réelles traitées en post (contraste extrême, grain, teinte vert/sépia)
- Dessins par-dessus les photos : silhouettes, annotations griffonnées, formes ambiguës
- Interface rétro point & click années 90 : boîte de dialogue en bas, portrait pixel art, œil en haut à droite
- Typographie : VT323 + Press Start 2P
- Scanlines, dithering, vignette, curseur crosshair

---

## Gameplay

- Point & click : zones cliquables sur les photos pour se déplacer ou inspecter
- Pas de HUD, pas d'inventaire
- Chaque inspection → fragment de texte cryptique (parle de toi, jamais de l'objet)
- Progression : X inspections dans une pièce → nouvelle zone débloquée
- Une zone verrouillée (█████) dès le début — révélée plus tard

---

## Narration

Texte court, jamais explicatif. Le texte pose des sensations, pas des réponses.

Exemples de ton :
- *Tu étais là avant que la maison existe.*
- *Ils t'appellent infestation. Tu t'appelles présence.*
- *Le plancher connaît leur poids par cœur. Pas le tien. Tu n'en as pas.*

---

## Structure des scènes (draft)

| Zone | Statut | Notes |
|------|--------|-------|
| Couloir | draft | scène de départ |
| Cuisine | draft | — |
| Chambre | draft | — |
| ████ | verrouillé | révélation finale |

---

## Stack technique

- Web / navigateur (pas de moteur de jeu)
- HTML + CSS + JS vanilla
- Assets : photos réelles + dessins par-dessus (couche SVG)
- Déploiement : Vercel ou itch.io

---

## Répartition

| Tâche | Qui |
|-------|-----|
| Photos (lieux, éclairage) | Kenny + Alexandra |
| Dessins par-dessus | Alexandra |
| Textes narratifs | Kenny + Alexandra |
| Dev (moteur, intégration) | Kenny |
| Direction artistique | Alexandra |

---

## Assets à créer

- [ ] Photos brutes des pièces (couloir, cuisine, chambre, ?)
- [ ] Traitement post (contraste, grain, teinte verte)
- [ ] Dessins par-dessus — couche 1 par scène minimum
- [ ] Textes d'intro par scène (1-2 phrases)
- [ ] Textes d'inspection par objet (2 variantes par objet)

---

## Refs

- *I Live Under Your House* — ambiance, design, palette
- *Disco Elysium* — narration intérieure cryptique
- *Yume Nikki* — exploration sans explication
- Esthétique EGA / DOS horror
