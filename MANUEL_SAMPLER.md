# Sampler de PianoToLife — Manuel d'utilisation

*Version 10.5.3 · [English version](SAMPLER_MANUAL.md) · Manuel général : [Manuel d'utilisation](MANUEL.md)*

Le sampler intégré de PianoToLife joue **vos propres échantillons de piano**, avec tous les moteurs de PianoToLife
par-dessus. Ce manuel explique comment transformer un dossier d'échantillons en piano jouable, ce que fait chaque
bouton, et comment en tirer le meilleur.

---

## Sommaire

1. [Le principe : des notes pédale levée, tout le reste modélisé](#1-le-principe--des-notes-pédale-levée-tout-le-reste-modélisé)
2. [Démarrage rapide : un piano en 10 étapes](#2-démarrage-rapide--un-piano-en-10-étapes)
3. [Préparer vos échantillons](#3-préparer-vos-échantillons)
4. [La fenêtre EDIT](#4-la-fenêtre-edit)
5. [Les outils de mapping, dans l'ordre conseillé](#5-les-outils-de-mapping-dans-lordre-conseillé)
6. [Les réglages de chaque touche](#6-les-réglages-de-chaque-touche)
7. [Enregistrer et gérer les sets](#7-enregistrer-et-gérer-les-sets)
8. [La fenêtre MIX : micros et streaming](#8-la-fenêtre-mix--micros-et-streaming)
9. [Jouer le sampler](#9-jouer-le-sampler)
10. [Fichiers et dossiers](#10-fichiers-et-dossiers)
11. [Dépannage](#11-dépannage)
12. [Diffuser des pianos échantillonnés](#12-diffuser-des-pianos-échantillonnés)

---

## 1. Le principe : des notes pédale levée, tout le reste modélisé

Un piano échantillonné demande en général des milliers de fichiers : notes pédale enfoncée, échantillons de
relâchement, résonance, bruits de pédale… PianoToLife n'a besoin que **des notes pédale levée**. Tout ce qui se
passe autour de la frappe est **modélisé en direct** :

- la résonance sympathique des cordes libres ;
- la pédale de sustain, la demi-pédale et le bruit de pédale ;
- l'una corda (pédale douce) ;
- le relâchement, les étouffoirs et la vélocité de relâchement ;
- les notes répétées (une nouvelle frappe ne coupe pas la précédente).

Une banque de **3 à 6 couches de vélocité** suffit : PianoToLife lisse les marches entre les couches pour qu'elle
joue comme un piano très échantillonné. Les banques profondes (60 couches, plusieurs micros, des dizaines de
gigaoctets) sont lues depuis le disque en streaming et jouent tout aussi bien.

---

## 2. Démarrage rapide : un piano en 10 étapes

1. En haut de la fenêtre principale, passez **HOST / SAMPLER** sur **SAMPLER**, puis ouvrez **EDIT**.
2. Cliquez sur **NEW** pour un set vide.
3. Choisissez le micro (**MIC 1** pour une banque à un seul micro).
4. **Déposez vos échantillons** n'importe où sur la fenêtre : fichiers WAV, AIFF, FLAC ou `.ncw` de Kontakt, un
   dossier entier (sous-dossiers compris ; les releases, bruits, notes pédale enfoncée et una corda sont écartés
   d'après leur nom), un `.sfz` ou un `.dspreset` de Decent Sampler. PianoToLife écoute chaque échantillon, trouve sa touche et place les
   couches de vélocité. Une barre de progression suit l'import ; cliquez sur la ligne d'état pour l'arrêter.
5. Pour les autres positions de micro, choisissez **MIC 2**, **MIC 3**… et déposez leurs échantillons de la même
   façon.
6. Cliquez sur **AUTO DYN** : PianoToLife écoute le A4, place ses couches sur l'intensité d'un vrai piano à queue,
   puis cale toutes les touches de la même façon.
7. Cliquez sur **FIX STEPS** : les frontières orange et rouges entre couches deviennent vertes.
8. Cliquez sur **ALIGN ATTACKS** : chaque frappe démarre au même instant, quels que soient la couche et le micro.
9. Cliquez sur **BALANCE ▸ Smooth** : le volume est régulier d'une touche à l'autre.
10. Cliquez sur **SAVE SET...** (activez d'abord **FLAC** si vous voulez un fichier plus petit, sans aucune perte).
    Votre piano est prêt : choisissez-le dans la liste SAMPLER de la fenêtre principale et réglez ses micros dans
    **MIX**.

Chaque outil a son **UNDO** (Cmd / Ctrl + Z) et son **REDO** (Maj + Cmd / Ctrl + Z).

---

## 3. Préparer vos échantillons

**Quoi enregistrer ou rassembler**

- **Uniquement des notes pédale levée**, une frappe par fichier, assez longue pour entendre l'extinction.
- Autant de couches de vélocité par touche que vous voulez. Plus il y en a, mieux c'est, mais 3 couches jouent déjà
  bien.
- Autant de touches que vous voulez : une banque échantillonnée toutes les 2 ou 3 notes est complétée par
  **FILL GAPS**.
- Jusqu'à **5 positions de micro** (une par MIC).

**Formats** : WAV, AIFF, FLAC et `.ncw` de Kontakt (10.3.5), mono ou stéréo, toute résolution. Les échantillons
au-dessus de 48 kHz sont convertis en 44,1 / 48 kHz à l'enregistrement du set (un piano n'a rien d'utile au-dessus de
20 kHz) ; les `.ncw` sont toujours réécrits en WAV ou FLAC dans le set. Les banques chiffrées ne sont pas lues :
n'utilisez que des banques dont la licence le permet. Toutes les analyses (touche, niveau, brillance) se font **en
stéréo**, canal par canal : une touche en opposition de phase entre deux micros espacés est mesurée comme on l'entend.

**Nommer vos fichiers** (facultatif mais conseillé). PianoToLife trouve la touche d'après le son lui-même, mais un
nom clair rend tout plus sûr :

| Quoi | À écrire comme un mot séparé | Exemple |
|---|---|---|
| La touche | nom de note ou numéro MIDI (seul, ou collé après des lettres) | `Piano_C4_mf.wav`, `Piano_F#7_p.wav`, `Piano_060_mf.wav`, `Piano-NP60-103.wav` |
| La couche : nuance | `ppp pp p mp mf f ff fff` | `Steinway_C4_mp.wav` |
| La couche : plage de vélocité | `1-12`, `033-064` | `Steinway_C4_033-064.wav` |
| La couche : vélocité | `v64`, `vel64` | `Steinway_C4_v64.wav` |
| La couche : numéro | `layer3`, `L3`, `VL3`, `dyn3` | `Steinway_C4_L3.wav` |
| La couche : vélocité juste après la touche (10.3.8) | un nombre après la note | `Piano-A2-40.wav`, `Piano-NP60-103.wav` |
| La couche : n'importe quel nombre qui suit l'intensité (10.3.8) | trouvé en comparant les nombres avec les niveaux mesurés des couches (un numéro de prise ou un temps de marteau, dans un sens ou dans l'autre) | `Piano_B3_M1_138_126.wav` |

Utilisez **un seul style pour toute la banque**. Un micro (`mic2`) n'est jamais lu comme une couche. Les **round
robins** (`rr2`, `seq2`, ou un dernier nombre juste après la touche quand le nom porte une couche :
`Piano_Dyn1_21_02`) sont écartés après le premier : REP donne à chaque frappe sa propre variation. Les noms de notes en
minuscules fonctionnent aussi (`f#7`, `c8`) ; une touche écrite `109` est lue comme C8. Des noms décalés d'une ou deux
octaves pour toute la banque (A0 nommé `A-2` ou `A-1`) sont corrigés à l'import. Avec AUTO LAYERS désactivé, les
vélocités écrites dans les noms deviennent les plages des couches : de chaque nombre jusqu'au suivant, ou — quand les
nombres finissent à 127 et qu'aucun ne vaut 1 — jusqu'à chaque nombre (la vélocité à laquelle la couche a été
enregistrée).

**Les banques imparfaites ne posent pas de problème.** PianoToLife gère les banques normalisées (chaque couche
remontée au même pic), mal coupées (frappes jusqu'à 1,5 s en retard, débuts coupés dans le son), nommées avec une ou
deux octaves de décalage, ou dont les micros ont été coupés séparément. Les notes aiguës très douces, où le bruit du
marteau dure plus que la corde, sont vérifiées sur leurs 150 premières ms (10.3.8).

---

## 4. La fenêtre EDIT

### La carte

La grande grille montre les **88 touches** (horizontalement) et les **vélocités 1 à 127** (verticalement). Chaque
rectangle est une **zone** : un échantillon, sur une touche, pour une plage de vélocités. La grille montre le micro
choisi avec **MIC 1 à 5**.

La ligne entre deux couches d'une touche est colorée selon la **marche de timbre** entendue quand on joue de part et
d'autre : **vert** sous 2 dB, **orange** sous 5 dB, **rouge** au-dessus.

**Souris et clavier**

| Action | Comment |
|---|---|
| Sélectionner des zones | Glisser n'importe où pour tracer un rectangle (comme Kontakt) ; un clic sélectionne une zone ; Maj ajoute ou retire |
| Déplacer des zones | Glisser une zone sélectionnée (blanche) |
| Changer les vélocités | Glisser le bord haut ou bas d'une zone sélectionnée ; ou flèches Haut / Bas (bord haut), Alt / Option + flèches (bord bas), Maj = 10 à la fois |
| Étirer un échantillon sur les touches voisines | Cmd / Ctrl + glisser sur le côté (Cmd / Ctrl + clic : sans étirement) |
| Supprimer | Suppr / Retour arrière : les zones sélectionnées ; sans sélection : toutes les couches de la touche choisie (ce MIC) |
| Afficher en jouant | **SHOW BY MIDI** activé (10.4.3) : la touche jouée s'affiche dans le panneau de droite, avec une ligne rouge dans la zone qui a sonné à cette vélocité, et la vélocité jouée à côté du nombre de couches (10.4.6). La sélection ne change pas. |
| Écouter un échantillon | Clic droit dessus dans le panneau latéral ou dans la grille (▶ vert) ; nouveau clic droit = arrêt |

Le **panneau latéral** montre dans son titre la touche, le micro et le nombre de couches qui y sont placées (10.4.2), puis les zones de la touche choisie : plage de vélocités, gain, fichier, touche entendue et
son accord en cents, sa brillance, la vélocité dont elle a le timbre, la marche avec la couche du dessous, et où se
trouve sa frappe. Une zone **orange** signale que la touche entendue diffère du nom de fichier : vérifiez-la. Dans le
panneau latéral (10.3.8), un **clic** sur un échantillon le sélectionne (surligné), la souris **dessus** affiche ses
informations (fichier, format audio, touche, vélocités, gain, niveau, brillance, accord, frappe) et un **clic droit**
le fait entendre seul. Une longue liste défile avec la molette ou les lignes ▲ / ▼, et suit la sélection.

**Ce qu'on entend en EDIT** (10.3.8) : le micro affiché (MIC 1 à 5) seul et neutre — 0 dB, centré, pleine largeur,
sans délai, sans L↔R, BODY à 0 — quel que soit le MIX. De retour dans la fenêtre principale, le MIX reprend la gestion
des micros.

### Les options du haut

| Option | Ce qu'elle fait | Par défaut |
|---|---|---|
| **Référence** (Grand D / Grand B / Upright) | Le piano dont les courbes d'intensité et de brillance servent à placer les couches et leurs gains | Grand B |
| **AUTO KEY** | Chaque échantillon va sur la touche de son son (vérifiée avec le nom de fichier). Désactivé : touche du nom de fichier, sinon là où on le dépose | Activé |
| **AUTO LAYERS** | Plages de vélocité et gains placés sur la référence. Désactivé : les couches d'une touche se partagent les vélocités à parts égales (ou prennent les plages écrites dans les noms) | Activé |
| **Samples** (auto / Normalised / Not normalised, 10.3.8 ; à côté d'AUTO LAYERS depuis la 10.4.6) | Comment AUTO LAYERS et AUTO DYN rangent et placent les couches d'une touche. **Not normalised** (la banque garde sa dynamique) : selon leurs niveaux, sur la courbe d'intensité de la référence. **Normalised** (chaque couche remontée au même niveau) : selon leur brillance. **Auto** : selon les niveaux quand les couches de la touche ont plus de 12 dB d'écart. En auto, AUTO DYN traite aussi le A4 comme normalisé quand ses couches culminent au même niveau. Un changement replace toutes les touches (les touches réglées à la main sont gardées) | Auto |
| **AUTO NAME** | Les nuances, vélocités ou numéros de couche des noms de fichier fixent l'ordre des couches (plus sûr quand deux couches se ressemblent) | Activé |
| **SOFT TIMBRE** + COLOR | Une note jouée sous la vélocité de sa couche prend le timbre plus sombre d'une frappe plus douce (la couleur 2–4 kHz et 4–8 kHz du piano de référence, mesurée sur chaque touche et chaque vélocité), pas seulement un niveau plus bas : des pp sous la couche la plus douce et des frontières lisses. COLOR (−100 à +100 %) dose l'effet | Activé, 0 % |
| **HARD TIMBRE** + COLOR | Une note jouée au-dessus de la vélocité de sa couche devient plus brillante, comme une frappe plus dure sur le piano de référence (mesuré sur chaque touche, jusqu'à +18 dB) : avec peu de couches, les vélocités intermédiaires sonnent comme de vraies frappes. Pour une couche du haut qui n'est pas vraiment fff, ou un set avec peu de couches | Désactivé, 0 % |
| **FADE IN** | Chaque échantillon commence par un fondu de 1 ms : un début coupé dans le son ne claque jamais | Désactivé |
| **FLAC** | Au prochain SAVE SET, les échantillons sont stockés compressés sans aucune perte (identiques au bit près, souvent 3 à 6 fois plus petits). Désactivé = WAV tels quels | Désactivé |

**SOFT TIMBRE / HARD TIMBRE et leur COLOR**

| Réglage | SOFT TIMBRE | HARD TIMBRE |
|---|---|---|
| Case décochée | Aucun effet, quel que soit COLOR | Aucun effet, quel que soit COLOR |
| COLOR **0 %** | **Actif, tel que mesuré** : une note jouée sous la vélocité de sa couche prend le timbre plus sombre d'une frappe plus douce ; à cette vélocité ou au-dessus, rien ne change | **Actif, tel que mesuré** : au-dessus de la vélocité de la couche, l'éclaircissement du piano de référence à cette vélocité (environ deux fois plus en 4–8 kHz qu'en 2–4 kHz) |
| COLOR au-dessus de 0 | Plus feutré : chaque note sonne comme une frappe jusqu'à 24 vélocités plus douce, même à la vélocité de sa couche | Plus brillant : commence jusqu'à 24 vélocités plus bas |
| COLOR entre 0 et −100 % | Moins d'assombrissement | Moins d'éclaircissement |
| COLOR **−100 %** | **Aucun effet** (comme décoché) | **Aucun effet** (comme décoché) |

0 % ne veut donc pas dire « éteint » mais « tel que mesuré sur le piano de référence ». Pour couper un effet, décochez
sa case ou mettez son COLOR à −100 %. Avec SOFT TIMBRE activé, on n'entend plus les sauts entre les couches de
vélocité.

---

## 5. Les outils de mapping, dans l'ordre conseillé

Les outils sont dans la barre du bas. Avec des zones sélectionnées, la plupart agissent **sur leurs touches
seulement** ; sans sélection, **sur toutes les touches** du micro affiché. AUTO DYN agit toujours sur toutes les
touches. **SHOW BY MIDI** ne sélectionne rien : cliquez dans une partie vide de la grille pour vider la sélection
avant de travailler sur toutes les touches.

1. **AUTO DYN** (appelé RECAL A4 avant la 10.4.2) — écoute le A4 aux 127 vélocités, place ses couches là où leur intensité les met sur la courbe de
   référence, les met à niveau, puis donne à chaque touche qui a le même nombre de couches les plages de vélocité du
   A4 et l'écoute de la même façon. Il mesure aussi l'accord du A4 (envoyé à SR A4 Tuning : 440 Hz joue le set tel
   qu'il a été enregistré). Fonctionne sur les banques normalisées (en crête ou en volume) : il lit alors l'attaque et
   la brillance de chaque couche au lieu de son niveau. Il suit le réglage **Samples** (10.4.6). Depuis la 10.5.1, il
   écoute avec SOFT / HARD COLOR tels qu'ils sont joués, et quand deux couches douces ou plus seraient entassées sous
   v16 (un pp enregistré plus doux que ce que joue la référence), elles sont réparties régulièrement de v1 jusqu'à la
   première couche au-dessus, leurs gains calés sur la courbe de référence (Dynamics ne change pas ; le souffle d'une
   couche très douce monte avec son gain).
2. **FIX STEPS** — déplace les frontières orange et rouges vers la vélocité où les deux timbres se rejoignent,
   lissée sur les touches voisines. À lancer **après** AUTO DYN (AUTO DYN replace les frontières selon l'intensité).
3. **ALIGN ATTACKS** — trouve la frappe dans chaque échantillon et fait démarrer chaque couche et chaque micro 3 ms
   avant : plus de flottement quand la nuance change, des micros en phase. Les fichiers ne sont pas modifiés.
4. **FILL GAPS** — chaque touche sans échantillon est jouée par la touche échantillonnée la plus proche, transposée
   (la moitié de l'écart de chaque côté). Les échantillons propres d'une touche gagnent toujours.
5. **BALANCE** — égalise le volume d'une touche à l'autre, mesuré à la vélocité 127 (les couches de chaque touche
   suivent).
   - **Smooth** : la courbe propre du set, sans les sauts (l'équilibre grave-aigu de l'enregistrement est gardé).
   - **Grand D / Grand B / Upright** : l'équilibre grave-aigu d'un piano de référence, au niveau de votre set.

   Il règle le gain des touches (au plus ±6 dB) ; plages de vélocité, gains des couches et dynamique ne sont pas
   touchés.
6. **AUTO RELEASE** — le temps de relâchement de chaque touche, mesuré sur un piano de concert (380 à 510 ms jusqu'à
   −60 dB), Infinite au-dessus de **Undamped Keys Above**. Ce réglage est aussi dans le panneau de touche
   (**Undamped**, le même que celui de la fenêtre principale) ; bougé à la main, les touches qui le franchissent
   reçoivent de nouveau AUTO RELEASE (10.3.8).
7. **LEVEL** et **AUTO** — le niveau de tout le set ; AUTO fait culminer la note la plus forte à la vélocité 127 à
   −9 dBFS (de la marge pour les accords, la résonance et le relâchement).
8. **AUTO COLOR** (10.5.1) — règle SOFT COLOR et HARD COLOR pour que la brillance des couches suive la couleur du piano
   de référence, du piano au forte (mesurée sur A2, A3, A4, A5 à 13 vélocités, 2–4 et 4–8 kHz, comme sur la référence ;
   seule la forme compte, un piano peut rester plus clair ou plus sombre dans l'ensemble). SOFT / HARD TIMBRE activés.
   À lancer **en dernier** : AUTO DYN → FIX STEPS → AUTO COLOR (à relancer après un AUTO DYN). UNDO remet les curseurs.

---

## 6. Les réglages de chaque touche

Choisissez une touche (ou plusieurs zones) et utilisez les boutons du panneau de touche. Ils s'appliquent à toutes
les couches des touches choisies.

| Bouton | Ce qu'il fait |
|---|---|
| **Gain** | Niveau de la touche, −24 à +12 dB (BALANCE l'écrit) |
| **Dynamics** | 100 % = la plage dynamique du piano de référence. Moins : plage plus étroite (notes douces plus fortes) ; plus : plus large |
| **Attack** | Temps de montée, 0 = l'échantillon tel qu'enregistré |
| **Decay** / **Sustain** | Temps pour atteindre le niveau Sustain ; 0 = l'extinction naturelle de l'échantillon |
| **Release** | 0 = **Auto** (le modèle d'étouffoirs de PianoToLife ; sans étouffoir au-dessus de Undamped Keys Above) ; un temps en ms ; tout à droite = **Infinite** (sans étouffoir : touches aiguës non étouffées) |
| **Tune** | Accord fin en cents |
| **LP** + fréquence + **LP Vel** | Passe-bas optionnel par voix ; LP Vel assombrit les notes douces (jusqu'à 3 octaves plus bas à 100 %) |
| **Undamped** | Undamped Keys Above, pour tout le piano (le réglage de la fenêtre principale, synchronisé) : les touches au-dessus n'ont pas d'étouffoir |

---

## 7. Enregistrer et gérer les sets

| Bouton | Ce qu'il fait |
|---|---|
| **NEW** | Un set vide (le set ouvert n'est pas modifié sur le disque) |
| **Nom** (sous le titre) | Cliquez pour **RENOMMER** le set et son fichier d'échantillons |
| **SAVE SET...** | Enregistre le set dans votre bibliothèque : la carte (`.ptlset`) et ses échantillons dans un conteneur chiffré (`.wptl`), réécrit seulement quand les échantillons changent |
| **SAVE AS VARIANT** | Un autre set sur **les mêmes échantillons** (partage le `.wptl`, sans copie), par exemple une version brillante et une version sombre |
| **PASSWORD...** | Protège EDIT par un mot de passe (jouer le set ne le demande jamais). Vide = pas de mot de passe |
| **CLEAR ALL** (10.4.3) | Vide tout le set (toutes les touches, tous les micros), après un avertissement qui donne le nombre d'échantillons. UNDO le remet ; les fichiers ne sont pas touchés |
| **DELETE** | Supprime les zones sélectionnées (voir le tableau plus haut) |
| **BACK** | Revient à la fenêtre principale |

Un set enregistré sur Mac s'ouvre sur Windows et inversement. Enregistrer un preset en mode SAMPLER crée un **preset
`[SAMP]`** qui contient le mapping et le modèle de résonance ; seuls les échantillons (`.wptl`) restent à part.

---

## 8. La fenêtre MIX : micros et streaming

### Micros

Chacun des 5 micros a sa tranche : **nom** (double-clic pour renommer), **ON** (un micro éteint n'est pas chargé :
ni mémoire, ni CPU), **solo**, **mute**, **L↔R** (inverse l'image stéréo : vue du pianiste ou du
public), **niveau**, **panoramique**, **largeur**, **délai** (pour aligner un micro
lointain sur les micros proches, ou garder son retard naturel de salle) et un indicateur **TRUE PEAK** (rouge = il a
saturé ; cliquez pour le remettre à zéro). Mixages tout prêts : **Close**, **Player**, **Hall** (toucher un réglage
le fait passer en Custom).

**ALL MICS TRUE PEAK** surveille les 5 micros ensemble. **BODY** règle la taille perçue du piano (aussi sur la
fenêtre principale).

### Streaming

Les grands sets sont joués depuis le disque : seul le début de chaque échantillon reste en mémoire.

| Réglage | Ce qu'il fait | Par défaut |
|---|---|---|
| **Disk** | Où sont vos échantillons : Auto (mesuré), SSD, HDD, Slow | Auto |
| **Preload** | Début de chaque échantillon gardé en mémoire ; Auto suit le disque (SSD 16 Ko, HDD 64 Ko, Slow 128 Ko) | Auto |
| **Cache** | Mémoire partagée par les voix qui jouent, pour ce qui vient du disque ; plus grand = moins de décrochages avec beaucoup de voix | 128 Mo |
| **Per key** | Combien de frappes d'une même touche peuvent sonner ensemble (notes répétées sous la pédale) | 4 |
| **Voices** | Polyphonie, tous micros confondus (2 micros = 2 voix par note). Une fois atteinte, la voix la plus faible s'éteint en 8 ms | 256 (Max 512) |
| **Test again** | Mesure le disque à nouveau (par exemple après avoir déplacé les échantillons) | |

**LIBRARY** choisit le dossier de vos sets (mettez-le sur votre disque le plus rapide). Avec l'option de copie,
SAVE SET copie les échantillons dans un dossier `Samples` à côté du set.

---

## 9. Jouer le sampler

En mode SAMPLER, les moteurs de PianoToLife jouent sur vos échantillons :

- **Résonance sympathique**, avec le Piano Model (`.srpiano`) du piano : capturez-en un depuis votre set (Capture),
  pour que la résonance ait la couleur de votre piano. En mode SAMPLER, la capture lit directement les échantillons,
  hors temps réel, aux centres de vos couches : quelques minutes au lieu d'un enregistrement en temps réel.
- **Sustain** : toujours Host Sustain en SAMPLER, avec une **demi-pédale** native sur les voix elles-mêmes
  (Progressive, ou Switch pour les pédales tout-ou-rien). La pédale tonale fonctionne.
- **Una corda** : simulée sur chaque voix (niveau et partiels d'une vraie una corda, plus le halo de la corde non
  frappée).
- **Relâchement** : les étouffoirs de PianoToLife ; avec un clavier qui envoie une vélocité de relâchement, un
  relâchement lent pose l'étouffoir plus tard (voir Keyboard Note-Off Floor et Curve dans la partie KEYBOARD).
- **Notes répétées** : une nouvelle frappe ne coupe pas la précédente ; celle-ci continue un peu plus bas (Per key
  dans MIX).
- **Répétition de piano réel (REP)**, sous CAL : au lieu des round robins des anciennes banques d'échantillons
  (plusieurs enregistrements de chaque note, joués à tour de rôle), chaque frappe reçoit les petites différences d'un
  vrai piano — niveau, brillance, extinction, attaque, un très léger désaccord dans le grave, et la montée d'une
  touche refrappée pendant qu'elle sonne — mesurées sur la référence choisie (Grand D / Grand B / Upright).
  Désactivé par défaut ; enregistré dans les presets ([Manuel d'utilisation](MANUEL.md#répétition-de-piano-réel-rep)).
- **Accord** : SR Transpose, SR Fine Pitch et SR A4 Tuning agissent sur le sampler.
- **BODY** : la taille perçue du piano.

**Détecteur de couches** (à côté de Capture) : joue une note aux 127 vélocités et liste les vraies couches du piano,
pour vérifier un set. **LEVEL TEST** : joue A0, C2, C4, C6 et C8 à la vélocité 127 et indique si le piano sature.

---

## 10. Fichiers et dossiers

| Fichier | Ce que c'est |
|---|---|
| `.ptlset` | Le set : la carte, les réglages des touches et les options (léger) |
| `.wptl` | Les échantillons, dans un conteneur chiffré (à côté du set) |
| Preset `[SAMP]` | Un preset du mode SAMPLER : mapping + modèle de résonance ; double-cliquez dessus (standalone) ou déposez-le sur la fenêtre |

Gardez le dossier d'un piano complet (preset, `.ptlset`, `.wptl`) : il peut alors être déplacé ou sauvegardé tel
quel.

**Échantillons introuvables** : si une session ou un preset désigne un piano dont les échantillons ont été effacés,
déplacés ou sont sur un disque non branché, une fenêtre propose de les **LOCATE** (PianoToLife retient le nouvel
emplacement) ou de **FORGET** ce piano (il n'est alors plus demandé).

---

## 11. Dépannage

| Problème | Solution |
|---|---|
| Un échantillon est sur la mauvaise touche ou octave | Vérifiez les zones orange dans le panneau latéral ; mettez la note dans le nom de fichier (`C4`, `060`) ; AUTO KEY activé |
| Deux couches sont dans le mauvais ordre | AUTO NAME avec les nuances dans les noms ; sinon déplacez-les à la main |
| Des marches en jouant crescendo (frontières orange / rouges) | AUTO DYN, puis FIX STEPS ; SOFT TIMBRE activé ; HARD TIMBRE pour une couche du haut trop sombre |
| Certaines touches plus fortes que leurs voisines | BALANCE ▸ Smooth (ou un piano de référence) |
| Un clic au début de certaines notes | ALIGN ATTACKS ; FADE IN pour les débuts coupés dans le son |
| Des notes en retard ou qui flottent entre les couches | ALIGN ATTACKS |
| Décrochages ou craquements avec beaucoup de notes | MIX : Test again, un Cache plus grand, un cran de Preload en plus, moins de Voices, ou les échantillons sur un SSD |
| Le piano sature | LEVEL ▸ AUTO ; surveillez TRUE PEAK dans MIX ; LEVEL TEST |
| « Sample set not found » | LOCATE le dossier, ou FORGET le piano |

Un clavier ou une banque qui se comporte à sa façon ? Contactez-moi avec une explication (un export du moniteur MIDI
est idéal).

---

## 12. Diffuser des pianos échantillonnés

Créer des sets avec PianoToLife et les jouer pour votre propre usage est gratuit. **Toute diffusion publique d'un
piano échantillonné fait pour le sampler de PianoToLife** (sets, fichiers `.ptlset` / `.wptl`, presets `[SAMP]`),
**gratuite ou payante, demande mon autorisation préalable.** Contactez-moi à
[olivier.frappier@live.fr](mailto:olivier.frappier@live.fr) avant de publier quoi que ce soit : nous mettrons en
place ensemble sa protection (conteneur chiffré, mot de passe, licence au nom de l'acheteur) et sa diffusion.
