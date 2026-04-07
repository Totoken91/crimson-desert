# Sand Rite — Walkthrough complet pour Alexandra
## Tout ce qui se passe dans le jeu, scène par scène

---

## ROUTE OPTIMALE — Fin A (pas de divines)

### SCÈNE 01a — Les Dunes plates (départ)

**Tu te réveilles.** Désert de sable rouge-sang. Pas de souvenirs.

> *"Tu existes. C'est la seule certitude. Tout le reste est du sable."*

**Ce que tu vois :**
- Un rocher saillant en haut à gauche (la dune principale)
- Une empreinte de corps dans le sable en bas à droite
- L'horizon au centre (bande entre le sable et le ciel noir)
- Une sortie à droite (bloquée)

**Ce que tu fais :**

1. **Clic sortie droite** → *"Tu ne peux pas partir comme ça. Il fait trop froid."*

2. **Clic rocher** → ZOOM sur le rocher (image: `rocher-saillant.png`)
   - Maintenir le clic 3 secondes → tu te fracasses la tête dessus
   - L'image passe à `rocher-saillant-sang.png` puis `rocher-saillant-sang-2.png`
   - Secousse de l'écran, flash rouge
   - **+3 Douleur, -3 Vitalité** → [D:3 S:0 O:0 | Vit:7/10]
   - Retour par le bas

3. **Clic empreinte** → ZOOM sur l'empreinte (image: `empreinte-sable.png`)
   - > *"Quelqu'un s'est allongé ici. La forme est encore tiède."*
   - Clic sur l'empreinte → **+1 Souffle**
   - > *"La forme est la tienne. Les griffures aussi."*
   - [D:3 S:1 O:0 | Vit:7/10]
   - Retour par le bas

4. **Clic horizon** → transition vers 01b

**Panneau alchimie (actif en 01a) :** Armure de peau visible (D×1 S×1 O×1) — pas assez d'Organique.

---

### SCÈNE 01b — Les Dunes (profondeur)

**Premier passage — fatigue automatique :**
> *"L'air est plus lourd ici. Ou tu es plus vide. Il te manque quelque chose pour continuer."*

→ Le **Poumon** apparaît dans le cercle d'alchimie en 01a

**Ce que tu vois :**
- Un rocher avec des cheveux accrochés (bas-droite)
- Un petit tas d'os avec quelque chose de noir en dessous (centre-gauche)
- Une anomalie lumineuse dans le sable (cercle de cendre)
- L'horizon vers 01c

**Ce que tu fais :**

5. **Clic rocher cheveux** → ZOOM (image: `hair-rock.png`)
   - > *"Quelque chose pousse sur la pierre. Tu prends une mèche. Ça ramollit déjà entre tes doigts."*
   - **+1 Organique** [D:3 S:1 O:1 | Vit:7/10]
   - Cooldown 30s avant de pouvoir reprendre
   - Retour par le bas

6. **Clic plume noire** → ZOOM (image: `plume-memoire.png`)
   - > *"Des os. En dessous, quelque chose de noir. Trop propre pour être ici."*
   - > *"Une plume. Tu te souviens d'un oiseau. Noir. Immobile."*
   - Pas de ressource — **flag plume-noire-collectee**
   - → **Plume de mémoire** apparaît dans le cercle
   - Retour par le bas

7. **Clic anomalie** → **+1 Souffle** (unique)
   - > *"La cendre forme un cercle. Personne ne l'a tracé."*
   - [D:3 S:2 O:1 | Vit:7/10]

8. **Clic horizon** → *"Trop loin. Quelque chose manque à l'intérieur."* (bloqué sans Poumon)

9. **Retour 01a** (clic bas de la scène)

---

### RETOUR 01a — Premiers crafts

> *"Quelque chose a changé. Tu sens de nouvelles possibilités."*

**Crafts disponibles :** Armure de peau (D1 S1 O1), Poumon (D2 S1), Plume de mémoire (D1 O1)

10. **Craft Armure de peau** (D1 S1 O1) → [D:2 S:1 O:0 | Vit:7/10]
    - > *"Quelque chose t'enveloppe. Tu ne sais pas si c'est chaud ou si tu as juste oublié ce que froid voulait dire."*
    - **Exit droite → Cimetière débloquée**

11. **Craft Poumon** (D2 S1) → [D:0 S:0 O:0 | Vit:7/10]
    - > *"Tu inspires. Pour la première fois. L'air a un goût de cendre."*
    - **01c accessible via horizon en 01b**

12. **Aller en 01b → horizon → 01c**

---

### SCÈNE 01c — Les Dunes lointaines

> *"Horizon atteint. Premiers signes que quelque chose d'autre est là."*

**Ce que tu vois :**
- Un couteau fiché dans le sable à droite — trop droit, trop précis
- Une silhouette humaine déformée au loin — trop de membres
- Une masse organique qui pulse dans le sable à gauche (le coeur)

13. **Clic couteau** → ZOOM (canvas: lame propre, fichée verticalement)
    - > *"Le couteau était propre. Fiché trop droit. Trop précis."*
    - Clic → **+2 Douleur** pour seulement **-1 Vitalité** (ratio avantageux)
    - L'image se redessine avec du sang sur la lame
    - [D:2 S:0 O:0 | Vit:6/10]
    - → **Lien de nerfs** apparaît dans le cercle

14. **Clic entité** → ZOOM (canvas: silhouette floue impossible)
    - > *"Elle se tient mal. Trop de choses poussent dans la mauvaise direction."*
    - Clic → **+1 Souffle** (unique)
    - > *"Quelque chose s'échappe d'elle. Un souffle. Le sien ou le tien."*
    - [D:2 S:1 O:0 | Vit:6/10]

15. **Clic coeur** → ZOOM (canvas: masse organique semi-enterrée)
    - > *"Il bat encore. Pas vite. Pas régulièrement. Mais il bat."*
    - Clic → **+1 Organique** (cooldown 20s) + flag coeur-inspecte
    - → **Coeur reliquaire** apparaît dans le cercle
    - [D:2 S:1 O:1 | Vit:6/10]

16. **Retour 01b (bas) → retour 01a (bas)**

---

### RETOUR 01a — Craft Lien de nerfs

Il faut D3 O2. On a D2 O1. Farm nécessaire :
- Rocher → hold → D+1 (Vit:5) → [D:3 S:1 O:1]
- 01b cheveux (30s cooldown) → O+1 → [D:3 S:1 O:2]

17. **Craft Lien de nerfs** (D3 O2) → [D:0 S:1 O:0 | Vit:5/10]
    - > *"Tes mains tremblent. Quelque chose se reconnecte."*
    - **Cimetière → Maison débloquée**

18. **Exit droite → Cimetière**

---

### SCÈNE 02 — Le Cimetière d'os

> *"Des os. Partout. Certains ont des formes impossibles. Il y en a beaucoup. Trop pour être accidentel."*

**Ce que tu vois :** Champ d'ossements. 5 zones interactives.

19. **Clic amas d'os** → ZOOM (canvas: os enchevêtrés + crâne avec excroissances)
    - État 1 : clic → **+2 Organique**
    - > *"Les os cèdent. En dessous, quelque chose brille."*
    - Le zoom se redessine avec un trou lumineux
    - [D:0 S:1 O:2 | Vit:5/10]

20. **Clic amas à nouveau** (état 2) → **+1 Souffle** (du crâne)
    - > *"L'os a continué à pousser après. Après quoi — pas encore."*
    - → **Tuile de mémoire** apparaît dans le cercle
    - [D:0 S:2 O:2 | Vit:5/10]

21. **Clic mâchoire** → ZOOM (canvas: crâne incomplet + mâchoire séparée)
    - > *"Elle est séparée du reste. Proprement."*
    - > *"Comme si quelqu'un l'avait retirée avec soin."*
    - → **Mâchoire osseuse** apparaît dans le cercle

22. **Clic fissure organique** → ZOOM (canvas: fissure sombre, masse molle)
    - > *"Quelque chose respire là-dedans."*
    - > *"Ou c'est le souvenir de quelque chose qui respirait."*
    - → **Estomac** apparaît dans le cercle

23. **Os tranchants** → hold 3s → **+3 Douleur, -3 Vitalité**
    - [D:3 S:2 O:2 | Vit:2/10] ⚠ **Pixels noirs clignotent !**

24. **Fissure pulsante** (discrète, bas-droite) → **+1 Souffle**
    - > *"Elle bat. Comme si elle t'attendait. Quelque chose s'en échappe."*
    - [D:3 S:3 O:2 | Vit:2/10]

25. **Retour 01a** (gauche) pour crafter

---

### RETOUR 01a — Crafts Mâchoire + Estomac

26. **Craft Mâchoire** (D2 O2) → [D:1 S:3 O:0 | Vit:2/10]
27. Farm O : 01b cheveux (30s) → O+1, 01c coeur (20s) → O+1 → [D:1 S:3 O:2 | Vit:2/10]
28. **Craft Estomac** (S1 O2) → [D:1 S:2 O:0 | Vit:2/10]

29. **Cimetière → droite → Maison**

---

### SCÈNE 03 — La Maison délabrée

> *"Une maison. Elle ne devrait pas être là."*

**Ce que tu vois :** Maison en ruine, porte entrouverte, fenêtre brisée, végétation.

30. **Clic porte** → ZOOM (canvas: porte de bois gonflé)
    - > *"Tu reconnais cette pièce. Comme on reconnaît ses propres mains."*
    - Clic → **+2 Organique** + la porte s'ouvre → la Chose informe apparaît
    - [D:1 S:2 O:2 | Vit:2/10]

31. **Clic Chose informe** → ZOOM (canvas: masse organique difforme)
    - Besoin Mâchoire ✅ + Estomac ✅
    - > *"C'est immonde. C'est la chose la plus réelle que tu aies faite depuis le début."*
    - **+4 Vitalité ! Cap Douleur → 7 !**
    - [D:1 S:2 O:2 | **Vit:6/10**] ← LE RETOURNEMENT

32. **Clic fenêtre** → ZOOM (canvas: cadre tordu, éclats)
    - Hold → D+2 (Vit:4)
    - [D:3 S:2 O:2 | Vit:4/10]

33. **Clic cheminée** → ZOOM (canvas: cendres, os calcinés)
    - > *"Les os brûlent différemment des autres matières. Ils gardent la lumière plus longtemps."*
    - → **Mémoire cendreuse** apparaît

34. **Clic oeil dans le mur** → ZOOM (canvas: oeil humain incrusté dans la pierre)
    - > *"Il est intact. Quelqu'un l'a mis là. Avec soin."*
    - → **Oeil de substitution** apparaît

35. **Clic sol empreintes** → ZOOM (canvas: empreintes dans les deux sens)
    - > *"Une paire s'arrête au seuil et ne repart pas."*
    - **+1 Souffle** [D:3 S:3 O:2 | Vit:4/10]

36. **Clic jardin** → **+1 Organique** [D:3 S:3 O:3 | Vit:4/10]

37. **Retour 01a** pour crafter

---

### RETOUR 01a — Crafts finaux

38. **Craft Mémoire cendreuse** (D1) → [D:2 S:3 O:3 | Vit:4]
    - → **Lanterne d'os** apparaît

39. **Craft Oeil de substitution** (D2 O1) → [D:0 S:3 O:2 | Vit:4]
    - > *"Quelque chose s'ajuste. Le monde était déjà là. Il était juste incomplet."*
    - → **Entrée grotte visible dans le cimetière**

40. Farm D : rocher → D+2 (Vit:2) → [D:2 S:3 O:2]

41. **Craft Lanterne d'os** (D2 S1) → [D:0 S:2 O:2 | Vit:2]

42. **Cimetière → entrée grotte (visible maintenant) → Grotte**

---

### SCÈNE 04 — La Grotte

> *"L'obscurité est totale."*

Avec la lanterne : la grotte s'éclaire. Stalactites, feu éteint, outils, mur gravé au fond.

43. **Stalactite** → **+1 Douleur** (Vit:1) ⚠
44. **Feu éteint** → **+1 Souffle**
    - > *"Le feu est récent. Quelqu'un était là. Peut-être toi."*
45. **Outils au sol** → **+1 Organique**

46. **Clic mur du fond** → ZOOM (canvas: silhouettes gravées)
    - **Dissolution = 0.0** → Gravures génériques, silhouettes qui s'agrandissent
    - Mot gravé en bas : *"recommencer"*

### FIN A

> *"Quelque chose te reconnaît. Tu t'effaces."*

Fondu noir. Reset. Retour scène 01a.

> *"Tu existes. Encore."*

---

## ROUTE PIÈGE — Fin C (Ailes craftées trop tôt)

Même début que la route optimale jusqu'au craft du Poumon.

Après avoir collecté la plume en 01b :

**Le joueur craft Plume de mémoire** (D1 O1) → les **Ailes** apparaissent (D6 S1 O1).

Le joueur farm D (rocher) et craft les **Ailes** (D6 S1 O1) :
- **-6 Vitalité** pour le D
- **Dissolution +0.15** → Fin C verrouillée
- Vitalité restante insuffisante pour crafter tous les vitaux
- Le joueur meurt inévitablement en cours de route

### FIN C

Mur du fond → gravures personnalisées avec ses greffes (les ailes dessinées).

Il lévite. Ses bras d'abord. Ses jambes. S'écartèle.

> *"Ce n'est pas une punition. C'est une récolte. Tu avais planté plus que prévu. Le désert reprend ce qui lui appartient. Il te rendra. Comme toujours. En moins bon état. Comme toujours."*

Cut noir brutal. Reset total — toutes greffes perdues.

> *"Tu existes. Encore. Quelque chose manque. Deux choses. L'une était à toi. L'autre — tu n'es pas sûr."*

---

## ASSETS ALEXANDRA DOIT DESSINER

### Scènes principales (1280×720 ou équivalent)

| # | Scène | Description |
|---|-------|-------------|
| 1 | **01a** | ✅ FAIT — `desert-bg-1.png` — Dunes cramoisies avec rocher et empreinte |
| 2 | **01b** | ✅ FAIT — `01b.png` — Dunes plus plates, rocher chevelu à droite |
| 3 | **01c** | À FAIRE — Dunes plus sombres/froides, couteau fiché à droite, silhouette déformée au loin, masse organique pulsante à gauche dans le sable |
| 4 | **02 Cimetière** | À FAIRE — Champ d'ossements dense, os blancs/cramoisies, formes impossibles, crâne avec excroissances, fissures |
| 5 | **03 Maison** | À FAIRE — Maison délabrée en ruine, bois noirci, porte entrouverte, fenêtre brisée, végétation envahissante, sable qui monte sur les murs, cheminée |
| 6 | **04 Grotte (noir)** | À FAIRE — Ouverture de grotte, obscurité totale |
| 7 | **04 Grotte (éclairée)** | À FAIRE — Intérieur rocheux éclairé par la lanterne, feu éteint, outils organiques, mur gravé au fond |
| 8 | **05 Ciel** | À FAIRE — Ciel cramoisie pur, désert vu d'en haut, cercles dans le sable, failles lumineuses |

### Plans rapprochés / close-ups

| # | Nom | États | Description |
|---|-----|-------|-------------|
| 9 | **Rocher saillant** | ✅ 3 états FAITS | `rocher-saillant.png`, `sang.png`, `sang-2.png` |
| 10 | **Empreinte sable** | ✅ FAIT | `empreinte-sable.png` |
| 11 | **Rocher chevelu** | ✅ FAIT | `hair-rock.png` |
| 12 | **Plume sous les os** | ✅ FAIT | `plume-memoire.png` |
| 13 | **Couteau** | 2 états À FAIRE | Lame propre fichée → lame rougie, sol taché |
| 14 | **Entité difforme** | 2 états À FAIRE | Silhouette floue impossible → (post-divines) empreinte d'ailes dans le sable |
| 15 | **Coeur semi-enterré** | 2 états À FAIRE | Masse organique cramoisie qui pulse → trace vide dans le sable |
| 16 | **Amas d'os** | 2 états À FAIRE | Os enchevêtrés + crâne avec excroissances → trou lumineux au centre |
| 17 | **Crâne excroissances** | 1 état À FAIRE | Crâne avec pointes osseuses / cornes naissantes (visible dans le zoom amas) |
| 18 | **Mâchoire séparée** | 1 état À FAIRE | Crâne incomplet + mâchoire isolée à côté |
| 19 | **Fissure organique** | 1 état À FAIRE | Fissure dans le sol, masse sombre et molle dedans |
| 20 | **Porte maison** | 2 états À FAIRE | Bois gonflé entrouverte → intérieur visible avec Chose informe dans un coin |
| 21 | **Chose informe** | 2 états À FAIRE | Masse organique difforme qui pulse → trace au sol vide |
| 22 | **Fenêtre brisée** | 1 état À FAIRE | Cadre tordu, éclats de verre |
| 23 | **Cheminée** | 1 état À FAIRE | Cendres, os calcinés, forme étrange |
| 24 | **Oeil dans le mur** | 1 état À FAIRE | Mur de pierre, oeil humain intact incrusté, iris cramoisie |
| 25 | **Sol empreintes** | 1 état À FAIRE | Empreintes dans les deux sens, une paire qui s'arrête au seuil |
| 26 | **Feu éteint** | 1 état À FAIRE | Cendres, braises mortes, os calciné |
| 27 | **Outils au sol** | 1 état À FAIRE | Formes organiques allongées, teintes chair/os |
| 28 | **Mur gravures A** | 1 état À FAIRE | Silhouettes gravées, "recommencer" en bas |
| 29 | **Mur gravures C** | 1 état À FAIRE | Même mur mais une silhouette a les ailes du joueur dessinées |

### Récapitulatif

| Catégorie | Fait | À faire | Total |
|-----------|------|---------|-------|
| Scènes principales | 2 | 6 | 8 |
| Close-ups | 4 | 17 états | 21 |
| **TOTAL** | **6** | **23** | **29** |
