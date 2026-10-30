# PianoToLife — Manuel d'utilisation

*Version 10.5.2 · [English version](USER_MANUAL.md) · Mapping du sampler : [Manuel du sampler](MANUEL_SAMPLER.md)*

PianoToLife fait **se comporter un piano virtuel comme un vrai** : les cordes qui résonnent par sympathie, la pédale
de sustain et la demi-pédale, les étouffoirs, le relâchement, l'una corda, les bruits de la mécanique. Ce manuel
explique comment il fonctionne, comment l'installer et ce que fait chaque partie de la fenêtre.

---

## Sommaire

1. [Un seul moteur de modélisation, deux sources de son](#1-un-seul-moteur-de-modélisation-deux-sources-de-son)
2. [Pourquoi le sampler n'utilise que des notes pédale levée](#2-pourquoi-le-sampler-nutilise-que-des-notes-pédale-levée)
3. [Installation et premier lancement](#3-installation-et-premier-lancement)
4. [Mode HOST : préparer votre piano](#4-mode-host--préparer-votre-piano)
5. [Mode SAMPLER](#5-mode-sampler)
6. [Piano Models : calibrer la résonance](#6-piano-models--calibrer-la-résonance)
7. [Résonance sympathique](#7-résonance-sympathique)
8. [Pédales](#8-pédales)
9. [Relâchement et étouffoirs](#9-relâchement-et-étouffoirs)
10. [Clavier, vélocité et moniteur MIDI](#10-clavier-vélocité-et-moniteur-midi)
11. [Bruits, corps, salle et sortie](#11-bruits-corps-salle-et-sortie)
12. [Presets, lecteur MIDI et affichages](#12-presets-lecteur-midi-et-affichages)
13. [CPU et performances](#13-cpu-et-performances)
14. [Dépannage](#14-dépannage)

---

## 1. Un seul moteur de modélisation, deux sources de son

PianoToLife a deux modes, choisis en haut de la fenêtre :

| Mode | D'où vient la frappe | Ce qu'ajoute PianoToLife |
|---|---|---|
| **HOST** | Un plug-in de piano que vous avez déjà (AU ou VST3), hébergé dans PianoToLife | Tout le moteur de modélisation |
| **SAMPLER** | Vos propres échantillons de piano, joués par le sampler intégré de PianoToLife | Le même moteur de modélisation |

Dans les deux modes, **les mêmes moteurs** agissent sur le son :

- la **résonance sympathique** de chaque corde libre, nourrie par le vrai son des notes que vous jouez ;
- la **pédale de sustain** et la **demi-pédale**, le rattrapage de pédale, la pédale tonale, le re-pédalage ;
- les **étouffoirs et le relâchement** : le feutre qui se pose sur une corde qui vibre encore, selon la vitesse de
  votre relâchement ;
- l'**una corda** (pédale douce) ;
- les **bruits de touche et de pédale**, le **Felt-Contact**, **BODY**, l'**Ambience**, le **Piano Comp**, la
  **Reverb** et l'**Output Ceiling**.

Sur un vrai piano à queue, la résonance de sustain et la résonance sympathique sont **un seul et même phénomène** :
la pédale ne fait que lever tous les étouffoirs d'un coup.

| Ce que vous faites | Ce qui se passe dans le piano |
|---|---|
| Une touche tenue | Une corde est libre de vibrer |
| Un accord tenu | Quelques cordes sont libres |
| Pédale enfoncée | Toutes les cordes sont libres |
| Demi-pédale | Toutes les cordes sont libres, mais encore légèrement touchées par les étouffoirs |

PianoToLife modélise exactement cela, avec un seul moteur : c'est pourquoi les transitions, la demi-pédale et les
accords rattrapés par la pédale sonnent naturellement.

---

## 2. Pourquoi le sampler n'utilise que des notes pédale levée

Comme tout ce qui entoure la frappe est **modélisé**, le sampler n'a besoin que des **notes pédale levée** d'un
piano :

- les **échantillons pédale enfoncée** contiennent la résonance de tout l'instrument, *figée au moment de
  l'enregistrement*. PianoToLife construit cette résonance en direct, à partir des cordes réellement libres à chaque
  instant. Jouer les deux mettrait la résonance en double, et celle qui est figée ne suivrait pas votre pédale ;
- les **échantillons de relâchement** feraient double emploi avec les étouffoirs de PianoToLife, qui suivent la
  vitesse de votre relâchement et la pédale ;
- les **bruits de pédale et les échantillons de résonance** sont eux aussi modélisés, selon la course et la vitesse
  de la pédale.

C'est aussi pour cela qu'en mode HOST, PianoToLife vous demande de couper ces options dans votre piano (voir la
[partie 4](#4-mode-host--préparer-votre-piano)). Le résultat est **hybride** : le réalisme de vrais enregistrements
pour la frappe et son timbre, et un comportement physique, en direct, pour tout ce qui se passe autour, sans des
centaines d'échantillons en plus. Une banque pédale levée de 3 à 6 couches suffit.

Pour construire un piano à partir d'échantillons (import, mapping, couches, micros, streaming), voir le
**[Manuel du sampler](MANUEL_SAMPLER.md)**.

---

## 3. Installation et premier lancement

| | macOS | Windows |
|---|---|---|
| Système | macOS 14 ou plus récent, Apple Silicon | Windows 10 / 11, 64 bits |
| Formats | Audio Unit, VST3, application autonome | VST3, application autonome (ASIO) |
| Piano hébergé | AU ou VST3 compilé pour Apple Silicon | VST3 x64 |

Installez le paquet depuis la page [Releases](../../releases/latest), puis ouvrez PianoToLife dans votre DAW (comme
instrument) ou en application autonome. Dans l'application autonome, choisissez votre carte son et votre clavier MIDI
dans les réglages audio.

---

## 4. Mode HOST : préparer votre piano

1. Choisissez votre plug-in de piano dans la partie **HOST** (scan, liste, Add VST3) et ouvrez sa fenêtre.
2. **Dans le piano hébergé**, coupez :
   - toute option de résonance *sympathique*, *de cordes*, *de sustain* ou *de pédale* ;
   - toute **réverbération, effet et compression** (salles, ambiance, égaliseur, limiteur, élargisseur) :
     PianoToLife écoute le son **sec** pour nourrir les cordes ;
   - ce que demande le **mode de pédale** (voir plus bas).
3. Réglez **Undamped Keys Above** sur la dernière touche à étouffoir de ce piano (souvent G6 sur un piano de
   concert) ; avec un piano à basses étendues, descendez la poignée gauche de **Sustain Free To** jusqu'à C0.
4. Chargez ou capturez le **Piano Model** de ce piano ([partie 6](#6-piano-models--calibrer-la-résonance)).

Besoin d'une salle ou de compression ? Utilisez le **Piano Comp** et la **Reverb** de PianoToLife : ils viennent
après la résonance, donc tout l'instrument passe dans la même salle.

### Modes de pédale (HOST)

| Mode | Le piano reçoit la pédale ? | Pour | À couper dans le piano |
|---|---|---|---|
| **Host Sustain** (par défaut) | Non : PianoToLife tient les notes | La plupart des pianos, y compris ceux dont on ne peut pas couper les échantillons de sustain | Bruits de touche / de relâchement, résonance sympathique |
| **Host Sustain (stacked)** | Non | Les pianos qui jouent un bruit d'étouffoir ou de relâchement à chaque refrappe | Comme Host Sustain |
| **Host Sustain (strict)** | Non | Les banques scriptées qui ignorent une refrappe plus douce d'une note tenue | Comme Host Sustain |
| **Pass-through** | Oui : le piano gère ses étouffoirs | Les pianos dont vous préférez la demi-pédale et le re-pédalage | Échantillons de sustain, résonance sympathique (garder demi-pédale et re-pédalage) |

En Host Sustain, une note refrappée sous la pédale se comporte comme un marteau sur une corde qui vibre encore : une
frappe plus douce sonne par-dessus la précédente, une frappe au moins aussi forte la remplace, et chaque frappe reçoit
son propre Note Off. Changer de mode de pédale relève les pédales jusqu'à ce que vous bougiez à nouveau la pédale.

---

## 5. Mode SAMPLER

Passez **HOST / SAMPLER** sur SAMPLER : le piano hébergé est mis de côté et le sampler de PianoToLife joue vos sets
d'échantillons. Choisissez un set dans la liste, réglez ses micros et son streaming dans **MIX**, et mappez de
nouveaux pianos dans **EDIT**.

En mode SAMPLER, la pédale fonctionne toujours en **Host Sustain**, avec une **demi-pédale** native sur les voix
elles-mêmes, et l'una corda est toujours en **Simu**. Vos choix du mode HOST sont gardés pour quand vous y revenez.

Tout ce qui concerne la construction d'un set est dans le **[Manuel du sampler](MANUEL_SAMPLER.md)**.

---

## 6. Piano Models : calibrer la résonance

La résonance suit les partiels exacts de chaque corde, d'après un **Piano Model** (`.srpiano`) du piano joué.
**Capturez un modèle pour chaque piano que vous utilisez** : avec le modèle d'un autre piano, beaucoup de cordes ne
correspondent plus.

**Capture** joue les 88 notes pédale levée, une par une, analyse leurs partiels, leur accord, leur inharmonicité et
leur extinction, et enregistre de courtes frappes à jusqu'à 8 vélocités placées au milieu des vraies couches du piano.
Sur un piano hébergé, elle joue en temps réel (environ 35 minutes, une seule fois). En mode SAMPLER, elle **lit
directement les échantillons**, hors temps réel, aux centres des couches du set : quelques minutes.

Avant la capture :

- réglez le piano **aussi fort que possible sans saturer** (**LEVEL TEST** joue A0, C2, C4, C6, C8 à la vélocité 127
  et vous le dit) ;
- **aucune réverbération, compression ni effet**, rien d'autre que la note seule (échantillons de relâchement,
  résonance et bruits coupés) ;
- la **courbe de vélocité** du piano **linéaire** ;
- de préférence les **micros proches** (utilisez l'Ambience de PianoToLife pour la salle).

Chaque modèle est ramené au même niveau de résonance à son chargement ; chacun garde son caractère. Un modèle de piano
de concert est fourni.

**Détecteur de couches** : joue une note aux 127 vélocités et liste les vraies couches de vélocité du piano (export
en texte).

---

## 7. Résonance sympathique

Les réglages principaux :

| Réglage | Ce qu'il fait |
|---|---|
| **SYMPATHETIC RESONANCE** on / off | Tout le moteur (résonance et relâchement de PianoToLife) |
| **Resonance Level** | L'intensité de la résonance des cordes libres |
| **AUTO CAL** (10.5.0, à côté de Resonance Level) | Cale le 0 dB de Resonance Level sur le piano et le modèle de résonance chargés, en 3 s environ (A3 tenu sans le faire sonner, A4 joué une fois ; ne jouez pas pendant ce temps). La résonance garde alors le même niveau par rapport au son du piano, quels que soient le piano, son volume, le niveau du set ou le modèle. Le bouton s'allume quand une calibration est active et la ligne Piano Model l'affiche (par ex. AUTO CAL +4.8 dB) ; recliquez quand vous voulez pour recalibrer ; Resonance Level monte ou baisse toujours autour. HOST et SAMPLER gardent chacun leur calibration (la bonne s'applique quand vous changez de mode). Gardé dans le preset / la session ; DEFAULT remet les deux à 0. Après une capture, PianoToLife propose de le lancer sur le nouveau modèle. À relancer après un changement de piano, de volume ou de modèle |
| **Harmonic Balance** | La couleur de la résonance (partiels graves ↔ aigus) |
| **Fullness** / **Shimmer** | Combien les cordes libres répondent sur leurs partiels graves / aigus |
| **Undamped Keys Above** | Dernière touche à étouffoir : les cordes au-dessus sonnent librement, jamais étouffées. En SAMPLER, les touches au-dessus en release Auto n'ont pas d'étouffoir non plus ; le réglage est aussi dans le panneau de touche d'EDIT |
| **Sustain Free From / To** | La plage de cordes libérées par la pédale |
| **Inharmonicity** | L'étirement des partiels, tel que mesuré sur le piano |
| **Max Free Strings (CPU)** | Combien de cordes peuvent résonner en même temps |
| **Enable Multicore Processing** | Partage la résonance entre les cœurs du processeur (même son) |

Les réglages détaillés se replient dans un tiroir ; chacun affiche **Default** à sa valeur par défaut, et **DEFAULT**
les remet tous. **Full Piano / Piano Only / PianoToLife DSP Only** permet d'écouter le piano seul, ou seulement ce que
PianoToLife ajoute.

**Silent Key** (à côté de SYMPATHETIC RESONANCE) : un appui silencieux lève l'étouffoir sans jouer de note, la corde
est alors libre de résonner. **≤ 1** (par défaut), **≤ 2**, **≤ 3** = les notes à cette vélocité ou moins ;
**Disklavier / N1** = aftertouch polyphonique 127 / 0 ; **Off** = aucun.

**PANIC** (10.4.2, entre Silent Key et DEFAULT) : arrête d'un coup tout ce qui sonne — notes bloquées, résonance, voix
du sampler, salle et lecteur MIDI — et envoie au piano hébergé All Notes Off, All Sound Off et les pédales relevées.

---

## 8. Pédales

- **Demi-pédale** : résonance et étouffement suivent la pédale de façon continue. **Half Pedal Damping Start / Full**
  règlent où les étouffoirs commencent et cessent de toucher les cordes.
- **Pedal Catch** : enfoncez la pédale juste *après* les notes, et les cordes qui sonnent encore nourrissent les
  cordes libérées, plus ou moins selon la rapidité du rattrapage. **Held** : l'épanouissement des touches encore
  tenues quand la pédale descend.
- **Pedal Release Time** (80 ms par défaut) : la remontée la plus rapide d'une pédale relâchée, pour qu'une pédale
  tout-ou-rien ne coupe jamais le son sèchement.
- **Sustain : Progressive / Switch** : Switch pour les pédales qui doivent fonctionner en tout-ou-rien (64 et plus =
  enfoncée).
- La **pédale tonale** fonctionne dans tous les modes.
- **Una corda** : **Simu** fait marcher la pédale douce avec n'importe quel piano (une note plus douce et plus ronde,
  adaptée à chaque piano, et le halo de la corde non frappée) ; **BP** envoie la pédale au piano pour ses propres
  échantillons d'una corda.

---

## 9. Relâchement et étouffoirs

Quand une touche est relâchée ou que la pédale remonte, le feutre se pose sur une corde qui vibre et l'étouffe
progressivement : un contact léger éteint d'abord les partiels aigus, un contact franc arrête tous les partiels
ensemble.

| Réglage | Ce qu'il fait |
|---|---|
| **Release Level** | Le relâchement de PianoToLife (conseillé : coupez le relâchement dans votre piano et gardez celui-ci). Décochez-le pour garder le relâchement de votre piano, ou mélangez les deux |
| **Release Decay** | La longueur de la queue de relâchement (plus longue dans le grave) |
| **Release Weights** | La couleur du relâchement (100 % = partiels tels qu'enregistrés) |
| **Ring** | L'énergie qui passe dans les cordes aiguës non étouffées et la gamme duplex |
| **Damper Damping** / **Slope** | La vitesse à laquelle les étouffoirs arrêtent les cordes, plus lente dans le grave, plus rapide dans l'aigu |
| **Felt-Contact** | Le feutre qui touche une corde qui vibre encore, avec son volume et sa couleur |

---

## 10. Clavier, vélocité et moniteur MIDI

### Modes de clavier et vélocité de relâchement

| Mode de clavier | Pour |
|---|---|
| **Standard** (par défaut) | Tous les claviers : chaque relâchement est le relâchement normal calibré |
| **Release Velocity 1-127** | Les claviers qui mesurent la vitesse de relâchement des touches |
| **Kawai VPC1** | Le VPC1, dont la vélocité de relâchement plafonne vers 100 et tombe facilement à 1 |
| **N1X or others** | Les hybrides Yamaha qui envoient la position de la touche par aftertouch pendant qu'elle remonte |
| **Yamaha P-525** | La mesure du relâchement du P-525 |

Dans tous les modes sauf Standard, le relâchement passe par le **Keyboard Note-Off Floor** (1 à 16, 16 par défaut :
la valeur de votre relâchement le plus lent, jamais une note qui ne s'arrête plus) et la **Keyboard Note-Off Curve**,
sur l'échelle interne 0–64 de PianoToLife (64 = un relâchement normal ; depuis un clavier 1-127, 64 et plus = normal).
**Note-Off to Host** choisit ce que reçoit le piano hébergé : **Var** (la même valeur), **64** (toujours normal : pas
de double traitement), **127**, ou **Raw** (ce que le clavier a envoyé). **Disable Aftertouch** / **Disable CC19**
tiennent ces messages à l'écart du **piano hébergé seulement** : le moteur de PianoToLife (touches muettes,
relâchement N1X / P-525) et l'enregistreur MIDI les voient toujours.

### Vélocité

La courbe **VELOCITY** est une ligne de points à glisser (double-clic pour en ajouter ou en retirer un). **CURVE**
écrit rapidement une courbe douce ; **COPY** / **PASTE** l'échangent en texte : `Velocity = [x0, x1, …; y0, y1, …]`
(jouée → envoyée). **CAL** calibre la dynamique de votre piano sur un piano de concert, un piano à queue ou un droit,
d'après le résultat du détecteur de couches.

### Répétition de piano réel (REP)

Sur un vrai piano, deux frappes ne sonnent jamais tout à fait pareil, même à la même vélocité. Un piano échantillonné
rejoue exactement le même enregistrement à chaque frappe — l'effet « mitraillette » des notes répétées rapides. Le
vieux remède des banques d'échantillons est le **round robin** : plusieurs enregistrements de chaque note à chaque
vélocité, joués à tour de rôle — lourd, et rarement complet. **REP** (sous CAL : **Off / Grand D / Grand B / Upright**)
simule plutôt la répétition d'un vrai piano, avec les écarts d'une frappe à l'autre mesurés sur le piano de référence
choisi :

- **SAMPLER** : chaque frappe a ses petites différences de niveau, de brillance et d'extinction, une attaque un peu
  différente dans le grave et le médium, un très léger désaccord dans le grave ; une touche refrappée pendant qu'elle
  sonne encore (pédale enfoncée, répétitions rapides) monte comme sur la référence.
- **HOST** : le piano hébergé fait le son, seule la vélocité varie donc (environ 1, au plus 3 ; jamais hors de sa
  couche de vélocité, jamais sur une touche muette).

Désactivé par défaut ; enregistré dans les presets et les sessions (les anciens s'ouvrent avec REP sur Off) ; coupé
pendant les captures et les mesures. Choisissez la référence la plus proche de votre piano. Pour un piano qui varie
déjà ses frappes (un piano modélisé, ou une banque avec round robins), laissez REP sur Off.

### Moniteur MIDI

Trois colonnes sur la même ligne : ce qu'envoie votre **clavier** (Keyboard), ce que lit le **moteur** de PianoToLife
(Engine) — la vélocité de relâchement de chaque Note Off (avec le temps de relâchement mesuré sur un N1X ou un
P-525), l'aftertouch et le CC19 — et ce qui part vers le **piano hébergé** (Host). Les différences sont surlignées ; **Export...** enregistre un fichier texte, idéal pour
signaler un clavier qui se comporte à sa façon.

---

## 11. Bruits, corps, salle et sortie

| Partie | Ce qu'elle fait |
|---|---|
| **Key Noise** (GRAND / UPRIGHT) | La mécanique en bois des touches : marteau qui retombe, touche qui arrive en butée, répétition |
| **Pedal Noise** | Chocs de bois, feutres sur les cordes et cordes graves libérées, selon la course et la vitesse de la pédale |
| **BODY** | La taille perçue du piano (à gauche de SOFT) : la fondamentale de chaque note renforcée ou atténuée, en HOST et en SAMPLER |
| **Ambience** | Une salle autour de la résonance et du relâchement, quand vous jouez avec les micros proches |
| **Piano Comp**, **Reverb** | Placés après la résonance : tout l'instrument passe dedans |
| **EQ1 / EQ2** (10.4.2) | Cliquez sur **EQ** sous REVERB : les EQ prennent la place de COMP / REVERB (le même bouton les ramène). **EQ1 BEFORE FX** agit avant COMP et REVERB, pour façonner le timbre du piano ; **EQ2 AFTER FX** agit tout à la fin, avant le Ceiling, pour corriger un casque. Pour chacun : **dessinez sur la courbe** (double-clic = un nouveau point, glisser = fréquence et gain, molette sur un point = sa largeur Q, clic droit = le supprimer), PREAMP, RESET = à plat, ou **LOAD** un preset — un `ParametricEQ.txt` d'AutoEq (mesures d'oratory1990, cible Harman) ou un fichier Equalizer APO ; chargez les presets de casque dans EQ2 (désactivez-le pour un bounce ou sur enceintes). Jusqu'à 20 points chacun. Gardé dans le preset et la session |
| **Output Ceiling** | Limiteur de sécurité true peak transparent, avec TRUE PEAK MAX, LUFS et l'indicateur du limiteur (LIM) |

---

## 12. Presets, lecteur MIDI et affichages

- Les **presets** gardent tous les réglages ; les presets SAMPLER sont marqués `[SAMP]` et contiennent le mapping des
  échantillons et le modèle de résonance. Double-cliquez sur un preset (application autonome) ou déposez-le sur la
  fenêtre.
- **Lecteur / enregistreur MIDI** (application autonome) : **LOAD MIDI**, **PLAY**, **REC**, **BOUNCE** (en WAV) —
  pour comparer des réglages sur exactement la même interprétation. Après REC, la prise commence à votre première note
  ou pédale (les pédales déjà enfoncées sont gardées) ; recliquez sur REC et la fenêtre d'enregistrement s'ouvre ;
  PLAY joue la prise aussitôt. LOAD MIDI et l'enregistrement ouvrent le même dossier. **ENGINE MIDI REC** (sous
  Disable CC19, activé par défaut) : la prise est écrite telle que le moteur la joue — le relâchement converti dans
  chaque Note Off (64 = normal, en dessous = plus lent), la courbe de vélocité appliquée, tout l'aftertouch gardé
  (compatible Disklavier / N1). Désactivé : l'entrée brute du clavier. Dans PianoToLife, la prise se rejoue en mode
  N1X ou Release Velocity 1-127.
  **Listes de lecture** (10.4.2) : LOAD MIDI ouvre un menu — plusieurs fichiers MIDI d'un coup, un dossier, ou une
  liste **.m3u** ; les morceaux s'enchaînent, **◀ / ▶** passent au précédent / suivant, et le menu permet de lire la
  liste en boucle ou de l'enregistrer en .m3u. Un fichier manquant est sauté. BOUNCE enregistre le morceau chargé.
  **METRO** (10.4.2) : clic = métronome marche / arrêt (le bouton affiche le tempo) ; clic droit = tempo (30–360 BPM,
  TAP), mesure (aucune, 1/1, 2/2, 2/4, 3/4, 4/4, 5/4, 8/4, 3/8, 6/8, 7/8, 8/8, 9/8, 12/8 — premier temps accentué, les groupes plus légèrement), son (bois ou bip), volume et **décompte**. On l'entend seulement — jamais
  dans un bounce ni dans la prise MIDI. Métronome en marche, REC démarre sur une mesure (après une mesure de décompte
  si coché) et le tempo et la mesure sont écrits dans le fichier MIDI : la prise tombe sur la grille d'un DAW.
- **Vue compacte** : réduit l'interface à une petite barre pendant que vous jouez. Depuis la 10.4.2, elle garde aussi ce
  qui sert en jouant : le lecteur MIDI et METRO (application autonome), l'accord joué, un clavier éclairé et cliquable,
  TRUE PEAK et LUFS.
- **Vue de la mécanique des étouffoirs** : les étouffoirs et les cordes en direct (touches tenues en orange), sans
  coût CPU. Depuis la 10.4.0 :
  - **un clavier de 88 touches** sous les cordes s'allume avec elles ; sa couleur suit la vélocité (pâle = doux,
    orange plein = fort), plus pâle pour les notes gardées par la pédale. **Cliquez dessus pour jouer** : plus bas sur
    la touche = plus fort ; glissez sur les touches pour un glissando. Ces notes suivent le même chemin que votre
    clavier (HOST et SAMPLER, MIDI Monitor, ENGINE MIDI REC) ;
  - **l'accord joué**, en grand à gauche de BODY : les touches tenues et les notes que les pédales font sonner.
    Seuls des noms d'accords s'affichent (C, Am7, Cmaj7/E…). Un accord tenu à la main gauche reste affiché pendant
    une mélodie à la main droite, et se complète quand la mélodie l'enrichit.
- **Accessibilité** : l'interface fonctionne avec les lecteurs d'écran (Narrator / NVDA, VoiceOver) et au clavier.

---

## 13. CPU et performances

La charge CPU affichée par votre DAW **inclut le piano hébergé**. Le cas le plus lourd est un long glissando pédale
enfoncée (des centaines de partiels qui sonnent). Ce qui compte, c'est **aucun craquement ni message de surcharge**.
Si vous entendez des craquements : augmentez la taille du buffer, activez **Enable Multicore Processing**, puis baissez
**Max Free Strings (CPU)**. En mode SAMPLER, voir aussi les réglages de streaming dans MIX
([Manuel du sampler](MANUEL_SAMPLER.md#8-la-fenêtre-mix--micros-et-streaming)).
REP et SOFT / HARD TIMBRE ajoutent quelques filtres par voix en mode SAMPLER : un petit coût (quelques %).

---

## 14. Dépannage

| Problème | Solution |
|---|---|
| La résonance est faible ou sonne faux | Capturez un Piano Model de *ce* piano ; vérifiez que la résonance et les effets du piano sont coupés |
| La résonance sonne en double ou figée | Coupez les échantillons de sustain / pédale enfoncée et la résonance du piano (ou passez en Host Sustain) |
| Bruits de relâchement au mauvais moment | En Host Sustain, coupez les bruits de touche / de relâchement du piano |
| Des notes traînent après un relâchement lent | Keyboard Note-Off Floor (16 = le plus sûr) ; vérifiez le mode de clavier dans le moniteur MIDI |
| Une touche silencieuse joue | Liste Silent Key ; vérifiez les vélocités dans le moniteur MIDI |
| Saturation | LEVEL TEST ; Output Ceiling ; baissez le volume du piano |
| Craquements | Voir CPU et performances |

Un clavier ou un piano qui se comporte à sa façon ? Contactez-moi à
[olivier.frappier@live.fr](mailto:olivier.frappier@live.fr) avec une explication (un export du moniteur MIDI est
idéal).
