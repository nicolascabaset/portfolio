<div align="center">

# Portfolio — Nicolas Cabaset

**Élève-ingénieur ESTACA · CFD & aérodynamique**

<br>

<img src="assets/logos/liu.png" height="70" alt="Linköping University">&nbsp;&nbsp;&nbsp;&nbsp;
<img src="assets/logos/ayari.png" height="70" alt="Ayari F1 Madness">&nbsp;&nbsp;&nbsp;&nbsp;
<img src="assets/logos/estaca.png" height="70" alt="ESTACA">

<br><br>

<img src="assets/ligier/ligier_js21_track.png" width="70%" alt="Ligier JS21 en piste">

<br><br>

![Ansys Fluent](https://img.shields.io/badge/Ansys_Fluent-FFB71B?style=for-the-badge&logo=ansys&logoColor=black)
![ANSA](https://img.shields.io/badge/ANSA-005EB8?style=for-the-badge)
![ParaView](https://img.shields.io/badge/ParaView-3E5C9A?style=for-the-badge)
![SolidWorks](https://img.shields.io/badge/SolidWorks-D22630?style=for-the-badge&logo=dassaultsystemes&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Linux HPC](https://img.shields.io/badge/HPC-Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![Cura](https://img.shields.io/badge/Cura-Impression_3D-0C60B8?style=for-the-badge)

</div>

---

## 📑 Sommaire

**1) [Projet CFD LiU](#1-projet-cfd-liu--étude-cfd-sur-modèle-drivaer-avec-hpc) (en cours)** — *Outils : Ansys Fluent Standalone / ANSA / ParaView / HPC (Linux) / Python*
- [Nettoyage CAO](#-nettoyage-cao-ansa)
- [Mesh surfacique et préparation volumique](#-mesh-surfacique-et-préparation-volumique)
- [Mesh volumique](#-mesh-volumique-en-cours)
- [Automatisation](#%EF%B8%8F-automatisation-en-cours)
- [Suite du projet](#%EF%B8%8F-suite-du-projet)

**2) [Ayari Racing × ESTACA : Étude CFD Ligier JS21](#2-ayari-racing--estaca--étude-cfd-ligier-js21-pour-monaco)** — *Outils : Ansys Workbench (Fluent / Meshing) / SolidWorks / Python / Excel*
- [A) Optimisation aileron avant](#a-optimisation-aileron-avant)
- [B) Optimisation aileron arrière](#b-optimisation-aileron-arrière)

**3) [Amélioration de la soufflerie de HAN](#3-projets-à-han--amélioration-de-la-soufflerie-de-han)** — *Outils : SolidWorks Flow Simulation / SolidWorks CAO / Excel / Cura (impression 3D)*
- [A) Étude de faisabilité de l'intégration CFD complète du ventilateur](#a-étude-de-faisabilité-de-lintégration-cfd-complète-du-ventilateur)
- [B) Conception et intégration d'un profil aéro pour l'injection de fumée en soufflerie](#b-conception-et-intégration-dun-profil-aéro-pour-linjection-de-fumée-en-soufflerie)

---

## 1) Projet CFD LiU — Étude CFD sur modèle DrivAer avec HPC

<table>
<tr>
<td width="45%" align="center"><img src="assets/drivaer/drivaer_model.png" width="100%" alt="Modèle DrivAer"></td>
<td>

| | |
|---|---|
| **Date** | 01/09/2026 → maintenant 🟡 *en cours* |
| **Contexte** | Semestre d'échange (Linköping University) — projet du cours *Applied CFD* |
| **Rôle** | Co-responsable CFD et *CAD cleaning* |
| **Outils** | Ansys Fluent Standalone · ANSA · ParaView · HPC (Linux) · Python |

</td>
</tr>
</table>

> **🎯 Problématique et objectif :** partir d'un modèle de géométrie sale pour en faire une CFD sur un HPC et automatiser/généraliser son workflow.

### 🧹 Nettoyage CAO (ANSA)

**Actions**
- **Correction topologique** — élimination des surfaces sécantes et fermeture étanche de l'ensemble des trous de la géométrie.
- **Simplification géométrique** — lissage des zones complexes (ex. calandre) et suppression des appendices secondaires (ex. rétroviseurs) pour alléger la charge de calcul.
- **Traitement du contact au sol** — création de surfaces de contact sous les pneumatiques pour une transition propre entre la route et les roues.

**Livrable** — modèle CAO finalisé : géométrie propre, fermée et optimisée, prête à être importée dans le mailleur.

<table>
<tr>
<td align="center" width="50%"><img src="assets/drivaer/cad_wheel_contact.png" width="100%"><br><sub>Surface de contact pneu/sol pour assurer un bon maillage</sub></td>
<td align="center" width="50%"><img src="assets/drivaer/cad_grille.png" width="100%"><br><sub>Exemple de simplification : calandre simplifiée et fermée</sub></td>
</tr>
</table>

### 🔺 Mesh surfacique et préparation volumique

**Actions**
- **Maillage carrosserie** — maillage surfacique basé sur la courbure (fonction *curvature*) avec bornes min/max strictes des cellules.
- **Raffinement sur les roues** — ciblage de courbure avec taille maximale réduite et *growth rate* imposé.
- **Contrôle de qualité** — détection et amélioration ciblée des cellules de skewness > 0,95.
- **Zones d'influence** — trois volumes de raffinement emboîtés (BOI – *Bodies Of Influence*) pour guider le maillage volumique.

**Livrables**
- **Maillage surfacique validé** respectant des critères de qualité stricts.
- **Architecture de raffinement** : BOI prêts à contraindre la croissance du maillage 3D dans le sillage.

<table>
<tr>
<td align="center" width="50%"><img src="assets/drivaer/surface_mesh_boi.png" width="100%"><br><sub>Mesh surfacique avec représentation des BOI (bleu)</sub></td>
<td align="center" width="50%"><img src="assets/drivaer/domain_boi.png" width="100%"><br><sub>Domaine avec le mesh et les BOI (bleu)</sub></td>
</tr>
</table>

### 🧊 Mesh volumique *(en cours)*

**Actions**
- **Couches limites (prism layers)** — configuration différenciée des couches d'inflation selon les surfaces physiques.
- **Ciblage y+** — méthode *last ratio* sur la carrosserie et les roues pour un y+ constant et maîtrisé.
- **Transition au sol** — méthode *aspect ratio* sur la piste pour lisser la transition vers le flux libre.
- **Zones d'influence** — paramétrage des trois volumes de raffinement.

**À faire**
- [ ] Valider le mesh volumique (critère ICEM CFD, aspect ratio…)
- [ ] Script de maillage automatisé, applicable à d'autres géométries

### ⚙️ Automatisation *(en cours)*

Automatisation du workflow grâce à des scripts (maillage, solveur, post-traitement).

<p align="center">
<img src="assets/drivaer/fluent_meshing_script.png" width="75%" alt="Script de maillage Fluent"><br>
<sub><i>Ébauche de code « user-friendly » pour automatiser le maillage sous Fluent</i></sub>
</p>

### 🗺️ Suite du projet

- [ ] **Paramétrage solveur** : rotation des roues, vitesse de la route, conditions aux limites…
- [ ] **Script solveur** : lancer la simulation uniquement via un script, généralisé à d'autres géométries
- [ ] **Review de la simulation** avec analyse des résidus
- [ ] **Post-processing** avec ParaView

---

## 2) Ayari Racing × ESTACA — Étude CFD Ligier JS21 pour Monaco

<table>
<tr>
<td width="40%" align="center"><img src="assets/ligier/ligier_js21_rear.png" width="100%" alt="Ligier JS21"></td>
<td>

| | |
|---|---|
| **Date** | 15/10/2025 → 30/04/2026 |
| **Contexte** | Partenariat technique d'un an (ESTACA 4A) avec Soheil Ayari pour améliorer les performances aérodynamiques d'une F1 historique engagée au Grand Prix de Monaco |
| **Rôle** | Responsable des études CFD · Référent technique assurant la liaison entre les besoins du pilote et le groupe projet |
| **Outils** | Ansys Workbench (Fluent / Meshing) · SolidWorks · Python · Excel |

</td>
</tr>
</table>

### A) Optimisation aileron avant

> **🎯 Problématique et objectif :** optimiser l'angle d'attaque de l'aileron avant pour le GP de Monaco en fonction de sa hauteur au sol.

#### Étude paramétrique

**Actions**
- **Setup paramétrique de l'angle** — variation de l'angle d'attaque (plages validées via CAO).
- **Setup paramétrique de la hauteur** — variation de la hauteur de l'aileron par rapport au sol (plage discutée avec le pilote).

**Livrable** — plages d'angle et de hauteur possibles pour les différents tests.

<p align="center">
<img src="assets/ligier/front_wing_cad.png" width="55%"><br>
<sub><i>CAO de l'aileron avant montrant la plage d'angle imposée par le flap</i></sub>
</p>

#### Domaine, maillage et conditions aux limites

**Actions**
- **Simulation 2D** — configuration simplifiée de l'aileron isolé pour cibler l'impact de l'incidence.
- **Vitesse** — 30 m/s, fixée selon les besoins piste et pilote ; sol en paroi mobile (*moving wall*).
- **Domaine fluide** — dimensionné selon les recommandations (10c amont, 15c aval, 10c hauteur).
- **Maillage** — maillage quadrangle (3 zones de densité) avec couches limites pour garantir un y+ de 1.

**Livrable** — modèle numérique 2D maillé et paramétré.

<table>
<tr>
<td align="center" width="33%"><img src="assets/ligier/front_domain.png" width="100%"><br><sub>Domaine complet : vitesse à l'inlet, pression à l'outlet, domaine large pour éviter toute influence externe</sub></td>
<td align="center" width="33%"><img src="assets/ligier/front_mesh.png" width="100%"><br><sub>Maillage avec 3 zones d'influence</sub></td>
<td align="center" width="33%"><img src="assets/ligier/front_inflation.png" width="100%"><br><sub>Couches d'inflation pour un y+ de 1</sub></td>
</tr>
</table>

#### Vérification transitoire (transient vs steady)

**Actions**
- **Modèle** — k-ω SST, imposé par l'incapacité hardware d'utiliser un modèle supérieur.
- **Test en stationnaire** — observation d'oscillations dans le C<sub>l</sub> et les résidus.
- **Test en transitoire** — meilleure convergence constatée.
- **Comparaison** — les deux aboutissent au même C<sub>l</sub> (unique coefficient utile au vu de la demande pilote).

**Livrable** — validation du maintien des calculs en stationnaire pour des temps de résolution plus rapides (beaucoup de paramètres à tester).

<table>
<tr><th width="40%">Stationnaire</th><th>Transitoire</th></tr>
<tr>
<td align="center"><img src="assets/ligier/steady_residuals.png" width="80%"><br><img src="assets/ligier/steady_cl.png" width="80%"><br><sub>Résidus (haut, continuité en bleu) et C<sub>l</sub> (bas) : oscillations visibles</sub></td>
<td align="center"><img src="assets/ligier/transient_residuals.png" width="100%"><br><img src="assets/ligier/transient_cl.png" width="100%"><br><sub>Converge davantage : continuité à 1e-3 contre 1e-2 en steady</sub></td>
</tr>
</table>

#### Post-traitement

**Actions**
- **Choix de métrique** — focalisation sur la portance (C<sub>l</sub>) pour répondre au besoin d'appui maximal ; uniquement comparatif car C<sub>l</sub> 2D.
- **Script Python** — traitement du signal (exclusion du régime transitoire, moyenne sur cycles stabilisés via autocorrélation) pour récupérer le C<sub>l</sub> de chaque simulation après le batch de calcul.
- **Comparaison** — croisement des données de portance avec les angles et hauteurs testés.
- **Exploitation** — traduction des résultats en réglages physiques mesurables simplement (mètre ruban).

**Livrables** — courbes ci-dessous et rapport technique vulgarisé à destination du pilote.

<table>
<tr>
<td align="center" width="50%"><img src="assets/ligier/cl_vs_angle.png" width="100%"><br><sub>Coefficient de portance en fonction de l'angle d'attaque pour différentes hauteurs au sol</sub></td>
<td align="center" width="50%"><img src="assets/ligier/angle_clmax_vs_height.png" width="100%"><br><sub>Angle de C<sub>l</sub> max en fonction de la hauteur au sol : le pilote sait directement quel angle imposer selon la hauteur choisie le jour J</sub></td>
</tr>
</table>

#### Rétrospective

<table>
<tr>
<td width="50%" valign="top">

**Compétences clés développées**
- **Maîtrise logicielle** : prise en main et exploitation d'Ansys Fluent (Workbench).
- **Interface technique/client** : traduction des besoins en solutions techniques et restitution vulgarisée.
- **Optimisation des calculs** : choix des modèles physiques selon les contraintes hardware, ciblage y+.
- **Analyse et synthèse de données** : traitement automatisé via Python d'une campagne de **90 simulations**.

</td>
<td width="50%" valign="top">

**Axes d'amélioration**
- **Validation des solveurs** : étendre la comparaison steady/transient à plusieurs incidences, ou imposer le transitoire.
- **Précision numérique** : CFL, GCI, growth rate, skewness, résidus de continuité ≤ 1e-3.
- **Optimisation du maillage** : grossir le maillage loin de l'aileron.
- **Stabilisation des résultats** : prolonger les calculs transitoires.
- **Diversification des conditions** : balayer plusieurs vitesses d'écoulement.

</td>
</tr>
</table>

### B) Optimisation aileron arrière

> **🎯 Problématique et objectif :** optimiser la géométrie de l'aileron arrière de type Monaco pour le GP.

#### Étude paramétrique

**Actions**
- **Analyse réglementaire** — étude des contraintes imposant des distances d'écartement spécifiques.
- **Analyse des libertés (CAO)** — évaluation des mouvements et débattements permis par les différents éléments.

**Livrable** — tableau de paramétrage des plages géométriques admissibles :

| Paramètre | Plage |
|---|---|
| d1 | > 0 |
| d2 | [0 ; 600 mm] |
| Hauteur aile/sol | 1000 mm max |
| Plage angle flap | [0 ; 20°] |
| Angle d'attaque (α) | libre |

<table>
<tr>
<td align="center" width="50%"><img src="assets/ligier/rear_wing_cad.png" width="100%"><br><sub>CAO du double aileron arrière, spécifique à la Ligier JS21 de 1983 pour Monaco</sub></td>
<td align="center" width="25%"><img src="assets/ligier/flap_max.png" width="100%"><br><sub>Angle flap maxi</sub></td>
<td align="center" width="25%"><img src="assets/ligier/flap_min.png" width="100%"><br><sub>Angle flap mini</sub></td>
</tr>
</table>

<p align="center">
<img src="assets/ligier/rear_wing_distances.png" width="75%"><br>
<sub><i>Illustration des distances d1 et d2</i></sub>
</p>

#### Domaine, maillage et solveur

**Actions**
- **Configuration du domaine** — reprise de l'environnement 2D de l'aileron avant, ajusté aux nouvelles dimensions.
- **Maillage structuré** — paramètres identiques (zones d'influence, ciblage y+) à l'étude précédente.
- **Paramétrage physique** — même vitesse et modèle k-ω SST en régime stationnaire.

**Livrable** — environnement de simulation 2D complet et standardisé, calqué sur la méthodologie de l'aileron avant.

<table>
<tr>
<td align="center" width="50%"><img src="assets/ligier/rear_mesh.png" width="100%"><br><sub>Maillage avec 3 zones d'influence</sub></td>
<td align="center" width="50%"><img src="assets/ligier/rear_inflation.png" width="100%"><br><sub>Couches d'inflation pour un y+ de 1</sub></td>
</tr>
</table>

#### Post-traitement

**Actions**
- **Traitement automatisé** — réutilisation du script Python développé précédemment.
- **Analyse comparative** — évaluation des **40 configurations** simulées pour cibler l'appui maximal exigé par Monaco.
- **Choix de métrique** — C<sub>l</sub> uniquement, à titre comparatif (2D).

**Livrable** — sélection et validation du meilleur réglage aérodynamique pour le pilote.

<table>
<tr>
<td align="center" width="50%"><img src="assets/ligier/rear_base_velocity.png" width="100%"><br><b>Configuration de base — C<sub>l</sub> = 0,97</b></td>
<td align="center" width="50%"><img src="assets/ligier/rear_best_velocity.png" width="100%"><br><b>Meilleure des 40 — C<sub>l</sub> = 2,57</b></td>
</tr>
</table>

> On observe une utilisation complète des deux ailerons, contrairement à la configuration de base.

#### Rétrospective

<table>
<tr>
<td width="50%" valign="top">

**Compétences clés développées**
- **Conformité et intégration géométrique** : arbitrage entre réglementation technique et débattements réels autorisés par la CAO.
- **Robustesse paramétrique** : stratégie de maillage unique et fiable, s'adaptant sans erreur à toutes les variations géométriques.

</td>
<td width="50%" valign="top">

**Axes d'amélioration**
- **Interaction globale** : intégrer le reste de la voiture (roues tournantes, sillage).
- **Couplage aérothermique** : prendre en compte le flux thermique du capot moteur.
- **Modélisation 3D** : capturer l'effet de la différence de largeur entre les ailerons.
- **Validation des solveurs** : comparer transitoire et stationnaire.
- **Plan d'expériences (DOE)** : réduire le nombre de simulations.
- **Précision numérique** : CFL, GCI, growth rate…

</td>
</tr>
</table>

---

## 3) Projets à HAN — Amélioration de la soufflerie de HAN

<table>
<tr>
<td width="50%" align="center"><img src="assets/han/wind_tunnel.png" width="100%" alt="Soufflerie HAN"></td>
<td>

| | |
|---|---|
| **Date** | 01/02/2025 → 01/06/2025 |
| **Contexte** | Semestre d'échange (HAN University of Applied Sciences) — projet d'ingénierie à quasi plein temps (4 j/semaine) |
| **Rôle** | Responsable simulations CFD |
| **Outils** | SolidWorks Flow Simulation · SolidWorks CAO · Excel · Cura |

</td>
</tr>
</table>

### A) Étude de faisabilité de l'intégration CFD complète du ventilateur

> **🎯 Problématique et objectif :** évaluer la faisabilité d'un couplage CFD complet entre le ventilateur et le reste de la soufflerie afin d'identifier les axes d'amélioration.

#### Mesures de vitesses pour comparaison CFD/mesures

**Action** — définition d'une grille de points de mesure identique en réel et en CFD pour relever les vitesses en sortie de ventilateur au tube de Pitot.

**Livrable** — cartographie comparative des écarts de vitesse pour identifier les erreurs et leur ampleur.

<p align="center">
<img src="assets/han/measured_grid.png" width="55%"><br>
<sub><i>Vitesses moyennes réelles sur la grille de mesure (A1 en haut à gauche de la sortie du ventilateur, F5 en bas à droite)</i></sub>
</p>

#### Mise au point, stabilisation et comparaison simulation/réalité (SolidWorks)

**Actions**
- **Optimisation du maillage et des paramètres physiques** — raffinements itératifs post-calcul : y+ adéquat, interface rotor/stator, gradients élevés ; rugosité de paroi et modèle de rotation préconisé par le solveur.
- **Troubleshooting des crashs solveur** — diminution progressive de la vitesse de rotation et diagnostic géométrique pour simplifier des micro-détails bloquants.

<table>
<tr>
<td align="center" width="50%"><img src="assets/han/fan_mesh_refinement.png" width="100%"><br><sub>Raffinement autour des zones de fort gradient et de la limite zone fixe/tournante</sub></td>
<td align="center" width="50%"><img src="assets/han/solver_crash.png" width="100%"><br><sub>Crash solveur après 3 jours de calcul</sub></td>
</tr>
</table>

**Livrables**
- **Modèle stabilisé et étude des limites de calcul** — écarts majeurs entre CFD et mesures, et démonstration de l'impossibilité d'obtenir un modèle corrélé au réel avec les délais et un PC grand public.
- **Bilan méthodologique** — synthèse des verrous numériques et besoins matériels, ayant servi à recadrer la faisabilité pédagogique de ces simulations dans le cours de CFD de l'université.

<p align="center">
<img src="assets/han/cfd_vs_measure_diff.png" width="55%"><br>
<sub><i>Écart entre résultats CFD et mesures réelles, en %</i></sub>
</p>

#### Rétrospective

<table>
<tr>
<td width="50%" valign="top">

**Compétences clés développées**
- Identification des facteurs influençant la précision du calcul
- Compréhension des limitations hardware
- **SolidWorks Flow Simulation** : maillage, configuration du calcul et post-traitement, base pour aborder des solveurs plus avancés

</td>
<td width="50%" valign="top">

**Axes d'amélioration**
- **Ciblage plus rapide des bons paramètres** dès les premières itérations.
- **Transition vers un solveur CFD dédié** : meilleures couches d'inflation, accès à k-ω SST.
- **Étude de sensibilité du dispositif expérimental** : fixation instrumentée vs maintien manuel, position axiale.

</td>
</tr>
</table>

### B) Conception et intégration d'un profil aéro pour l'injection de fumée en soufflerie

> **🎯 Problématique et objectif :** concevoir le profil aérodynamique d'un *smoke rake* pour réduire sa traînée parasite et assurer l'injection d'un flux de fumée non perturbé.

#### Étude comparative, dimensionnement et sélection du profil

**Actions**
- **Présélection théorique et adaptation CAO** — sélection de 4 profils laminaires NACA série 6 symétriques (0 % de cambrure) à plus faible traînée, mis à l'échelle sous SolidWorks pour loger le smoke rake.

<p align="center">
<img src="assets/han/naca_63a010.png" width="70%"><br>
<sub><i>Exemple de profil retenu : 0 % de cambrure et faible traînée pour le Re de l'écoulement</i></sub>
</p>

- **Caractérisation CFD en sillage** — simulations à V∞ = 22,2 m/s et extraction des vitesses sur une grille identique en aval pour comparer la perturbation de chaque profil.

**Livrable** — matrice de vitesses et choix du profil perturbant le moins l'écoulement.

<table>
<tr>
<td align="center" width="50%"><img src="assets/han/wake_18pct.png" width="100%"><br><sub>Profil 18 % d'épaisseur</sub></td>
<td align="center" width="50%"><img src="assets/han/wake_10pct.png" width="100%"><br><sub>Profil 10 % d'épaisseur ✅</sub></td>
</tr>
</table>

<p align="center"><sub><i>F1 le plus proche du bord de fuite, A6 le plus loin. Choix du profil 10 % : vitesses plus proches de 22,2 m/s.</i></sub></p>

#### Optimisation aéro des buses d'injection et conception interne pour impression 3D

**Action** — étude paramétrique CFD sur l'implantation des buses (en retrait, affleurantes ou sortantes) et comparaison des profils de vitesse en sillage pour retenir la géométrie offrant le flux le plus régulier.

<p align="center">
<img src="assets/han/nozzle_cutplot.png" width="75%"><br>
<sub><i>Cut plot comparatif : configuration de buse à perturbation minimale vs configuration défavorable</i></sub>
</p>

**Livrable** — pièce imprimée en 3D ajustée sur le peigne, prête pour le lissage de surface avant les essais en soufflerie.

<p align="center">
<img src="assets/han/smoke_rake_print_1.png" height="260"> &nbsp;
<img src="assets/han/smoke_rake_print_2.png" height="260">
</p>

#### Rétrospective

<table>
<tr>
<td width="50%" valign="top">

**Compétences clés développées**
- **Dimensionnement aéro & CAO (SolidWorks)** : choisir un profil NACA et l'adapter sous contrainte d'encombrement.
- **Études paramétriques CFD** : comparer des champs de vitesse pour minimiser les perturbations.
- **Conception orientée intégration** : évider un volume intérieur, anticiper les jeux de montage.
- **Impression 3D (Cura)** : arbitrer entre finesse aérodynamique et contraintes d'impression.

</td>
<td width="50%" valign="top">

**Axes d'amélioration**
- **Intégrer l'épaisseur requise en amont** : présélectionner sur la traînée réelle Fx après mise à l'échelle plutôt que sur un Cx catalogue.
- **Élargir les critères CFD** : perte de pression totale et énergie cinétique turbulente (TKE).
- **Validation expérimentale en soufflerie** après lissage pour corréler la CFD.

</td>
</tr>
</table>

---

<div align="center">

📄 Portfolio complet : [`Portfolio_Cabaset_Nicolas.pdf`](Portfolio_Cabaset_Nicolas.pdf)

<sub>© Nicolas Cabaset</sub>

</div>
