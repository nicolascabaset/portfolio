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

<br>

<a id="sommaire"></a>

## 📑 Sommaire

<table>
<tr>
<td width="33%" align="center" valign="top">
<a href="#p1"><img src="assets/drivaer/drivaer_model.png" width="100%"></a><br>
<b><a href="#p1">1) Projet CFD LiU</a></b><br>
<sub>Étude CFD DrivAer avec HPC · <i>en cours</i></sub>
</td>
<td width="33%" align="center" valign="top">
<a href="#p2"><img src="assets/ligier/ligier_js21_rear.png" width="100%"></a><br>
<b><a href="#p2">2) Ayari Racing × ESTACA</a></b><br>
<sub>Étude CFD Ligier JS21 pour Monaco</sub>
</td>
<td width="33%" align="center" valign="top">
<a href="#p3"><img src="assets/han/wind_tunnel.png" width="100%"></a><br>
<b><a href="#p3">3) Soufflerie de HAN</a></b><br>
<sub>Amélioration de la soufflerie</sub>
</td>
</tr>
<tr>
<td valign="top">

- [Nettoyage CAO](#p1-1)
- [Mesh surfacique et préparation volumique](#p1-2)
- [Mesh volumique](#p1-3)
- [Automatisation](#p1-4)
- [Suite du projet](#p1-5)

</td>
<td valign="top">

- [A) Optimisation aileron avant](#p2a)
- [B) Optimisation aileron arrière](#p2b)

</td>
<td valign="top">

- [A) Faisabilité CFD complète du ventilateur](#p3a)
- [B) Profil aéro pour l'injection de fumée](#p3b)

</td>
</tr>
<tr>
<td align="center"><sub>Fluent Standalone · ANSA · ParaView · HPC · Python</sub></td>
<td align="center"><sub>Ansys Workbench · SolidWorks · Python · Excel</sub></td>
<td align="center"><sub>SolidWorks Flow Sim. · SolidWorks · Excel · Cura</sub></td>
</tr>
</table>

<br>

<!-- ═══════════════════════════════════════════════════════════════ -->

<a id="p1"></a>

<img src="assets/banners/p1_liu.png" width="100%" alt="1) Projet CFD LiU — Étude CFD sur modèle DrivAer avec HPC">

| 🏫 Contexte | 👤 Rôle | 🛠️ Outils |
|---|---|---|
| Semestre d'échange (Linköping University) — projet du cours *Applied CFD* | Co-responsable CFD et *CAD cleaning* | Ansys Fluent Standalone · ANSA · ParaView · HPC (Linux) · Python |

> [!IMPORTANT]
> **🎯 Problématique et objectif** — Partir d'un modèle de géométrie sale pour en faire une CFD sur un HPC et automatiser/généraliser son workflow.

<p align="center"><sub>ÉTAPES DU PROJET</sub><br>
<img src="https://img.shields.io/badge/1-Nettoyage_CAO-E8826A?style=flat-square" alt="1 · Nettoyage CAO"> ➜ <img src="https://img.shields.io/badge/2-Mesh_surfacique-E8826A?style=flat-square" alt="2 · Mesh surfacique"> ➜ <img src="https://img.shields.io/badge/3-Mesh_volumique-E8826A?style=flat-square" alt="3 · Mesh volumique"> ➜ <img src="https://img.shields.io/badge/4-Automatisation-E8826A?style=flat-square" alt="4 · Automatisation"> ➜ <img src="https://img.shields.io/badge/5-Suite-BBBBBB?style=flat-square" alt="5 · Suite">
</p>

<a id="p1-1"></a>

### <img src="https://img.shields.io/badge/%C3%89TAPE_1-Nettoyage_CAO_%28ANSA%29-E8826A?style=for-the-badge" alt="ÉTAPE 1 · Nettoyage CAO (ANSA)">

<table>
<tr>
<td width="50%" valign="top">

**⚙️ Actions**
- **Correction topologique** — élimination des surfaces sécantes et fermeture étanche de l'ensemble des trous de la géométrie.
- **Simplification géométrique** — lissage des zones complexes (ex. calandre) et suppression des appendices secondaires (ex. rétroviseurs) pour alléger la charge de calcul.
- **Traitement du contact au sol** — création de surfaces de contact sous les pneumatiques pour une transition propre entre la route et les roues.

</td>
<td width="50%" valign="top" align="center">
<img src="assets/drivaer/cad_wheel_contact.png" width="100%"><br><sub>Surface de contact pneu/sol pour assurer un bon maillage</sub><br><br>
<img src="assets/drivaer/cad_grille.png" width="100%"><br><sub>Exemple de simplification : calandre simplifiée et fermée</sub>
</td>
</tr>
</table>

> [!TIP]
> **✅ Livrable** — Modèle CAO finalisé : géométrie propre, fermée et optimisée, prête à être importée dans le mailleur.

<a id="p1-2"></a>

### <img src="https://img.shields.io/badge/%C3%89TAPE_2-Mesh_surfacique_et_pr%C3%A9paration_volumique-E8826A?style=for-the-badge" alt="ÉTAPE 2 · Mesh surfacique et préparation volumique">

<table>
<tr>
<td width="50%" valign="top">

**⚙️ Actions**
- **Maillage carrosserie** — maillage surfacique basé sur la courbure (fonction *curvature*) avec bornes min/max strictes des cellules.
- **Raffinement sur les roues** — ciblage de courbure avec taille maximale réduite et *growth rate* imposé.
- **Contrôle de qualité** — détection et amélioration ciblée des cellules de skewness > 0,95.
- **Zones d'influence** — trois volumes de raffinement emboîtés (BOI – *Bodies Of Influence*) pour guider le maillage volumique.

</td>
<td width="50%" valign="top" align="center">
<img src="assets/drivaer/surface_mesh_boi.png" width="100%"><br><sub>Mesh surfacique avec représentation des BOI (bleu)</sub><br><br>
<img src="assets/drivaer/domain_boi.png" width="100%"><br><sub>Domaine avec le mesh et les BOI (bleu)</sub>
</td>
</tr>
</table>

> [!TIP]
> **✅ Livrables**
> - **Maillage surfacique validé** — enveloppe discrétisée respectant des critères de qualité stricts.
> - **Architecture de raffinement** — BOI prêts à contraindre la croissance du maillage 3D dans le sillage.

<a id="p1-3"></a>

### <img src="https://img.shields.io/badge/%C3%89TAPE_3-Mesh_volumique-E8826A?style=for-the-badge" alt="ÉTAPE 3 · Mesh volumique"> <img src="https://img.shields.io/badge/EN_COURS-FF9800?style=for-the-badge" alt="en cours">

**⚙️ Actions**
- **Couches limites (prism layers)** — configuration différenciée des couches d'inflation selon les surfaces physiques.
- **Ciblage y+** — méthode *last ratio* sur la carrosserie et les roues pour un y+ constant et maîtrisé.
- **Transition au sol** — méthode *aspect ratio* sur la piste pour lisser la transition vers le flux libre et éviter les sauts de taille de mailles.
- **Zones d'influence** — paramétrage des trois volumes de raffinement.

> [!WARNING]
> **📝 À faire**
> - Valider le mesh volumique (critère ICEM CFD, aspect ratio…)
> - Script de maillage automatisé, applicable à d'autres géométries que la nôtre

<a id="p1-4"></a>

### <img src="https://img.shields.io/badge/%C3%89TAPE_4-Automatisation-E8826A?style=for-the-badge" alt="ÉTAPE 4 · Automatisation"> <img src="https://img.shields.io/badge/EN_COURS-FF9800?style=for-the-badge" alt="en cours">

Automatisation du workflow grâce à des scripts (maillage, solveur, post-traitement).

<p align="center">
<img src="assets/drivaer/fluent_meshing_script.png" width="80%" alt="Script de maillage Fluent"><br>
<sub><i>Ébauche de code « user-friendly » pour automatiser le maillage sous Fluent</i></sub>
</p>

<a id="p1-5"></a>

### <img src="https://img.shields.io/badge/%C3%89TAPE_5-Suite_du_projet-888888?style=for-the-badge" alt="ÉTAPE 5 · Suite du projet">

| | Tâche | Détail |
|:-:|---|---|
| ⬜ | **Paramétrage solveur** | Rotation des roues, vitesse de la route, conditions aux limites… |
| ⬜ | **Script solveur** | Lancer la simulation uniquement via un script, généralisé à d'autres géométries |
| ⬜ | **Review de la simulation** | Analyse des résidus |
| ⬜ | **Post-processing** | ParaView |

<p align="right"><a href="#sommaire">⬆️ Retour au sommaire</a></p>

<br>

<!-- ═══════════════════════════════════════════════════════════════ -->

<a id="p2"></a>

<img src="assets/banners/p2_ayari.png" width="100%" alt="2) Ayari Racing × ESTACA — Étude CFD Ligier JS21 pour Monaco">

| 🏫 Contexte | 👤 Rôle | 🛠️ Outils |
|---|---|---|
| Partenariat technique d'un an (ESTACA 4A) avec Soheil Ayari pour améliorer les performances aérodynamiques d'une F1 historique engagée au Grand Prix de Monaco | • Responsable des études CFD<br>• Référent technique assurant la liaison entre les besoins du pilote et le groupe projet | Ansys Workbench (Fluent / Meshing) · SolidWorks · Python · Excel |

<br>

<a id="p2a"></a>

<img src="assets/banners/p2a.png" width="100%" alt="A) Optimisation de l'aileron avant">

> [!IMPORTANT]
> **🎯 Problématique et objectif** — Optimiser l'angle d'attaque de l'aileron avant pour le GP de Monaco en fonction de sa hauteur au sol.

<p align="center">
<img src="https://img.shields.io/badge/1-%C3%89tude_param%C3%A9trique-1BA7B4?style=flat-square" alt="1 · Étude paramétrique"> ➜ <img src="https://img.shields.io/badge/2-Domaine_et_maillage-1BA7B4?style=flat-square" alt="2 · Domaine et maillage"> ➜ <img src="https://img.shields.io/badge/3-Steady_vs_transient-1BA7B4?style=flat-square" alt="3 · Steady vs transient"> ➜ <img src="https://img.shields.io/badge/4-Post--traitement-1BA7B4?style=flat-square" alt="4 · Post-traitement"> ➜ <img src="https://img.shields.io/badge/%E2%98%85-R%C3%A9trospective-555555?style=flat-square" alt="★ · Rétrospective">
</p>

#### <img src="https://img.shields.io/badge/%C3%89TAPE_1-%C3%89tude_param%C3%A9trique-1BA7B4?style=for-the-badge" alt="ÉTAPE 1 · Étude paramétrique">

<table>
<tr>
<td width="55%" valign="top">

**⚙️ Actions**
- **Setup paramétrique de l'angle** — variation de l'angle d'attaque (plages validées via CAO).
- **Setup paramétrique de la hauteur** — variation de la hauteur de l'aileron par rapport au sol (plage discutée avec le pilote).

</td>
<td width="45%" align="center">
<img src="assets/ligier/front_wing_cad.png" width="100%"><br><sub>CAO de l'aileron avant montrant la plage d'angle imposée par le flap</sub>
</td>
</tr>
</table>

> [!TIP]
> **✅ Livrable** — Plages d'angle et de hauteur possibles pour les différents tests.

#### <img src="https://img.shields.io/badge/%C3%89TAPE_2-Domaine%2C_maillage_et_conditions_aux_limites-1BA7B4?style=for-the-badge" alt="ÉTAPE 2 · Domaine, maillage et conditions aux limites">

**⚙️ Actions**
- **Simulation 2D** — configuration simplifiée de l'aileron isolé pour cibler l'impact de l'incidence.
- **Vitesse** — 30 m/s, fixée selon les besoins piste et pilote ; sol en paroi mobile (*moving wall*).
- **Domaine fluide** — dimensionné selon les recommandations (10c amont, 15c aval, 10c hauteur).
- **Maillage** — maillage quadrangle (3 zones de densité) avec couches limites pour garantir un y+ de 1.

<table>
<tr>
<td align="center" width="33%"><img src="assets/ligier/front_domain.png" width="100%"><br><sub>Domaine complet : vitesse à l'inlet, pression à l'outlet, domaine large pour éviter toute influence externe</sub></td>
<td align="center" width="33%"><img src="assets/ligier/front_mesh.png" width="100%"><br><sub>Maillage avec 3 zones d'influence</sub></td>
<td align="center" width="33%"><img src="assets/ligier/front_inflation.png" width="100%"><br><sub>Couches d'inflation pour un y+ de 1</sub></td>
</tr>
</table>

> [!TIP]
> **✅ Livrable** — Modèle numérique 2D maillé et paramétré.

#### <img src="https://img.shields.io/badge/%C3%89TAPE_3-V%C3%A9rification_transitoire_%28transient_vs_steady%29-1BA7B4?style=for-the-badge" alt="ÉTAPE 3 · Vérification transitoire (transient vs steady)">

**⚙️ Actions**
- **Modèle** — k-ω SST, imposé par l'incapacité hardware d'utiliser un modèle supérieur.
- **Test en stationnaire** — observation d'oscillations dans le C<sub>l</sub> et les résidus.
- **Test en transitoire** — meilleure convergence constatée.
- **Comparaison** — les deux aboutissent au même C<sub>l</sub> (unique coefficient utile au vu de la demande pilote).

<table>
<tr><th width="40%">📉 Stationnaire</th><th>📉 Transitoire</th></tr>
<tr>
<td align="center"><img src="assets/ligier/steady_residuals.png" width="80%"><br><img src="assets/ligier/steady_cl.png" width="80%"><br><sub>Résidus (haut, continuité en bleu) et C<sub>l</sub> (bas) : oscillations visibles</sub></td>
<td align="center"><img src="assets/ligier/transient_residuals.png" width="100%"><br><img src="assets/ligier/transient_cl.png" width="100%"><br><sub>Converge davantage : continuité à 1e-3 contre 1e-2 en steady</sub></td>
</tr>
</table>

> [!TIP]
> **✅ Livrable** — Validation du maintien des calculs en stationnaire pour des temps de résolution plus rapides (beaucoup de paramètres à tester).

#### <img src="https://img.shields.io/badge/%C3%89TAPE_4-Post--traitement-1BA7B4?style=for-the-badge" alt="ÉTAPE 4 · Post-traitement">

**⚙️ Actions**
- **Choix de métrique** — focalisation sur la portance (C<sub>l</sub>) pour répondre au besoin d'appui maximal ; uniquement comparatif car C<sub>l</sub> 2D.
- **Script Python** — traitement du signal (exclusion du régime transitoire, moyenne sur cycles stabilisés via autocorrélation) pour récupérer le C<sub>l</sub> de chaque simulation après le batch de calcul.
- **Comparaison** — croisement des données de portance avec les angles et hauteurs testés.
- **Exploitation** — traduction des résultats en réglages physiques mesurables simplement (mètre ruban).

<table>
<tr>
<td align="center" width="50%"><img src="assets/ligier/cl_vs_angle.png" width="100%"><br><sub>Coefficient de portance en fonction de l'angle d'attaque pour différentes hauteurs au sol</sub></td>
<td align="center" width="50%"><img src="assets/ligier/angle_clmax_vs_height.png" width="100%"><br><sub>Angle de C<sub>l</sub> max en fonction de la hauteur au sol : le pilote sait directement quel angle imposer selon la hauteur choisie le jour J</sub></td>
</tr>
</table>

> [!TIP]
> **✅ Livrables** — Les courbes ci-dessus et un rapport technique vulgarisé à destination du pilote.

#### <img src="https://img.shields.io/badge/%E2%98%85-R%C3%A9trospective-555555?style=for-the-badge" alt="★ · Rétrospective">

<table>
<tr>
<th width="50%">💪 Compétences clés développées</th>
<th width="50%">🔧 Axes d'amélioration</th>
</tr>
<tr>
<td valign="top">

- **Maîtrise logicielle** : prise en main et exploitation d'Ansys Fluent (Workbench).
- **Interface technique/client** : traduction des besoins en solutions techniques et restitution vulgarisée.
- **Optimisation des calculs** : choix des modèles physiques selon les contraintes hardware, ciblage y+.
- **Analyse et synthèse de données** : traitement automatisé via Python d'une campagne de **90 simulations**.

</td>
<td valign="top">

- **Validation des solveurs** : étendre la comparaison steady/transient à plusieurs incidences, ou imposer le transitoire.
- **Précision numérique** : CFL, GCI, growth rate, skewness, résidus de continuité ≤ 1e-3.
- **Optimisation du maillage** : grossir le maillage loin de l'aileron.
- **Stabilisation des résultats** : prolonger les calculs transitoires.
- **Diversification des conditions** : balayer plusieurs vitesses d'écoulement.

</td>
</tr>
</table>

<br>

<a id="p2b"></a>

<img src="assets/banners/p2b.png" width="100%" alt="B) Optimisation de l'aileron arrière">

> [!IMPORTANT]
> **🎯 Problématique et objectif** — Optimiser la géométrie de l'aileron arrière de type Monaco pour le GP.

<p align="center">
<img src="https://img.shields.io/badge/1-%C3%89tude_param%C3%A9trique-7A3FA6?style=flat-square" alt="1 · Étude paramétrique"> ➜ <img src="https://img.shields.io/badge/2-Domaine%2C_maillage%2C_solveur-7A3FA6?style=flat-square" alt="2 · Domaine, maillage, solveur"> ➜ <img src="https://img.shields.io/badge/3-Post--traitement-7A3FA6?style=flat-square" alt="3 · Post-traitement"> ➜ <img src="https://img.shields.io/badge/%E2%98%85-R%C3%A9trospective-555555?style=flat-square" alt="★ · Rétrospective">
</p>

#### <img src="https://img.shields.io/badge/%C3%89TAPE_1-%C3%89tude_param%C3%A9trique-7A3FA6?style=for-the-badge" alt="ÉTAPE 1 · Étude paramétrique">

<table>
<tr>
<td width="50%" valign="top">

**⚙️ Actions**
- **Analyse réglementaire** — étude des contraintes imposant des distances d'écartement spécifiques.
- **Analyse des libertés (CAO)** — évaluation des mouvements et débattements permis par les différents éléments.

**📐 Plages géométriques admissibles**

| Paramètre | Plage |
|---|---|
| d1 | > 0 |
| d2 | [0 ; 600 mm] |
| Hauteur aile/sol | 1000 mm max |
| Plage angle flap | [0 ; 20°] |
| Angle d'attaque (α) | libre |

</td>
<td width="50%" valign="top" align="center">
<img src="assets/ligier/rear_wing_cad.png" width="100%"><br><sub>CAO du double aileron arrière, spécifique à la Ligier JS21 de 1983 pour Monaco</sub><br><br>
<img src="assets/ligier/flap_max.png" width="45%"> <img src="assets/ligier/flap_min.png" width="45%"><br><sub>Angle flap maxi · Angle flap mini</sub>
</td>
</tr>
</table>

<p align="center">
<img src="assets/ligier/rear_wing_distances.png" width="75%"><br>
<sub><i>Illustration des distances d1 et d2</i></sub>
</p>

> [!TIP]
> **✅ Livrable** — Tableau de paramétrage : synthèse des plages de variation géométriques admissibles pour la simulation.

#### <img src="https://img.shields.io/badge/%C3%89TAPE_2-Domaine%2C_maillage_et_solveur-7A3FA6?style=for-the-badge" alt="ÉTAPE 2 · Domaine, maillage et solveur">

<table>
<tr>
<td width="50%" valign="top">

**⚙️ Actions**
- **Configuration du domaine** — reprise de l'environnement 2D de l'aileron avant, ajusté aux nouvelles dimensions.
- **Maillage structuré** — paramètres identiques (zones d'influence, ciblage y+) à l'étude précédente.
- **Paramétrage physique** — même vitesse et modèle k-ω SST en régime stationnaire.

</td>
<td width="50%" align="center">
<img src="assets/ligier/rear_mesh.png" width="100%"><br><sub>Maillage avec 3 zones d'influence</sub><br><br>
<img src="assets/ligier/rear_inflation.png" width="100%"><br><sub>Couches d'inflation pour un y+ de 1</sub>
</td>
</tr>
</table>

> [!TIP]
> **✅ Livrable** — Environnement de simulation 2D complet et standardisé, calqué sur la méthodologie de l'aileron avant.

#### <img src="https://img.shields.io/badge/%C3%89TAPE_3-Post--traitement-7A3FA6?style=for-the-badge" alt="ÉTAPE 3 · Post-traitement">

**⚙️ Actions**
- **Traitement automatisé** — réutilisation du script Python développé précédemment.
- **Analyse comparative** — évaluation des **40 configurations** simulées pour cibler l'appui maximal exigé par Monaco.
- **Choix de métrique** — C<sub>l</sub> uniquement, à titre comparatif (2D).

<table>
<tr>
<td align="center" width="50%"><img src="assets/ligier/rear_base_velocity.png" width="100%"><br><b>Configuration de base — C<sub>l</sub> = 0,97</b></td>
<td align="center" width="50%"><img src="assets/ligier/rear_best_velocity.png" width="100%"><br><b>🏆 Meilleure des 40 — C<sub>l</sub> = 2,57</b></td>
</tr>
</table>

> [!TIP]
> **✅ Livrable** — Sélection et validation du meilleur réglage aérodynamique pour le pilote. On observe une utilisation complète des deux ailerons, contrairement à la configuration de base.

#### <img src="https://img.shields.io/badge/%E2%98%85-R%C3%A9trospective-555555?style=for-the-badge" alt="★ · Rétrospective">

<table>
<tr>
<th width="50%">💪 Compétences clés développées</th>
<th width="50%">🔧 Axes d'amélioration</th>
</tr>
<tr>
<td valign="top">

- **Conformité et intégration géométrique** : arbitrage entre réglementation technique et débattements réels autorisés par la CAO.
- **Robustesse paramétrique** : stratégie de maillage unique et fiable, s'adaptant sans erreur à toutes les variations géométriques.

</td>
<td valign="top">

- **Interaction globale** : intégrer le reste de la voiture (roues tournantes, sillage).
- **Couplage aérothermique** : prendre en compte le flux thermique du capot moteur.
- **Modélisation 3D** : capturer l'effet de la différence de largeur entre les ailerons.
- **Validation des solveurs** : comparer transitoire et stationnaire.
- **Plan d'expériences (DOE)** : réduire le nombre de simulations.
- **Précision numérique** : CFL, GCI, growth rate…

</td>
</tr>
</table>

<p align="right"><a href="#sommaire">⬆️ Retour au sommaire</a></p>

<br>

<!-- ═══════════════════════════════════════════════════════════════ -->

<a id="p3"></a>

<img src="assets/banners/p3_han.png" width="100%" alt="3) Projets à HAN — Amélioration de la soufflerie de HAN">

| 🏫 Contexte | 👤 Rôle | 🛠️ Outils |
|---|---|---|
| Semestre d'échange (HAN University of Applied Sciences) — projet d'ingénierie à quasi plein temps (4 j/semaine) | Responsable simulations CFD | SolidWorks Flow Simulation · SolidWorks CAO · Excel · Cura (impression 3D) |

<br>

<a id="p3a"></a>

<img src="assets/banners/p3a.png" width="100%" alt="A) Faisabilité de l'intégration CFD complète du ventilateur">

> [!IMPORTANT]
> **🎯 Problématique et objectif** — Évaluer la faisabilité d'un couplage CFD complet entre le ventilateur et le reste de la soufflerie afin d'identifier les axes d'amélioration.

<p align="center">
<img src="https://img.shields.io/badge/1-Mesures_de_vitesses-D32F2F?style=flat-square" alt="1 · Mesures de vitesses"> ➜ <img src="https://img.shields.io/badge/2-Mise_au_point_CFD-D32F2F?style=flat-square" alt="2 · Mise au point CFD"> ➜ <img src="https://img.shields.io/badge/3-Comparaison_et_bilan-D32F2F?style=flat-square" alt="3 · Comparaison et bilan"> ➜ <img src="https://img.shields.io/badge/%E2%98%85-R%C3%A9trospective-555555?style=flat-square" alt="★ · Rétrospective">
</p>

#### <img src="https://img.shields.io/badge/%C3%89TAPE_1-Mesures_de_vitesses_pour_comparaison_CFD%2Fmesures-D32F2F?style=for-the-badge" alt="ÉTAPE 1 · Mesures de vitesses pour comparaison CFD/mesures">

<table>
<tr>
<td width="50%" valign="top">

**⚙️ Action** — Définition d'une grille de points de mesure identique en réel et en CFD pour relever les vitesses en sortie de ventilateur au tube de Pitot.

</td>
<td width="50%" align="center">
<img src="assets/han/measured_grid.png" width="100%"><br><sub>Vitesses moyennes réelles (m/s) — A1 en haut à gauche de la sortie du ventilateur, F5 en bas à droite</sub>
</td>
</tr>
</table>

> [!TIP]
> **✅ Livrable** — Cartographie comparative des écarts de vitesse pour identifier les erreurs et leur ampleur.

#### <img src="https://img.shields.io/badge/%C3%89TAPE_2-Mise_au_point_et_stabilisation_de_la_CFD_du_ventilateur_%28SolidWorks%29-D32F2F?style=for-the-badge" alt="ÉTAPE 2 · Mise au point et stabilisation de la CFD du ventilateur (SolidWorks)">

**⚙️ Actions**
- **Optimisation du maillage et des paramètres physiques** — raffinements itératifs post-calcul : y+ adéquat, interface rotor/stator, gradients élevés ; rugosité de paroi et modèle de rotation préconisé par le solveur.
- **Troubleshooting des crashs solveur** — diminution progressive de la vitesse de rotation et diagnostic géométrique pour simplifier des micro-détails bloquants.

<table>
<tr>
<td align="center" width="50%"><img src="assets/han/fan_mesh_refinement.png" width="100%"><br><sub>Raffinement autour des zones de fort gradient et de la limite zone fixe/tournante</sub></td>
<td align="center" width="50%"><img src="assets/han/solver_crash.png" width="100%"><br><sub>Crash solveur après 3 jours de calcul</sub></td>
</tr>
</table>

#### <img src="https://img.shields.io/badge/%C3%89TAPE_3-Comparaison_simulation%2Fr%C3%A9alit%C3%A9-D32F2F?style=for-the-badge" alt="ÉTAPE 3 · Comparaison simulation/réalité">

<table>
<tr>
<td width="50%" align="center">
<img src="assets/han/cfd_vs_measure_diff.png" width="100%"><br><sub>Écart entre résultats CFD et mesures réelles, en %</sub>
</td>
<td width="50%" valign="top">

> [!TIP]
> **✅ Livrables**
> - **Modèle stabilisé et étude des limites de calcul** — écarts majeurs entre CFD et mesures, et démonstration de l'impossibilité d'obtenir un modèle corrélé au réel avec les délais et un PC grand public.
> - **Bilan méthodologique** — synthèse des verrous numériques et besoins matériels, ayant servi à recadrer la faisabilité pédagogique de ces simulations dans le cours de CFD de l'université.

</td>
</tr>
</table>

#### <img src="https://img.shields.io/badge/%E2%98%85-R%C3%A9trospective-555555?style=for-the-badge" alt="★ · Rétrospective">

<table>
<tr>
<th width="50%">💪 Compétences clés développées</th>
<th width="50%">🔧 Axes d'amélioration</th>
</tr>
<tr>
<td valign="top">

- Identification des facteurs influençant la précision du calcul
- Compréhension des limitations hardware
- **SolidWorks Flow Simulation** : maillage, configuration du calcul et post-traitement, base pour aborder des solveurs plus avancés

</td>
<td valign="top">

- **Ciblage plus rapide des bons paramètres** dès les premières itérations.
- **Transition vers un solveur CFD dédié** : meilleures couches d'inflation, accès à k-ω SST.
- **Étude de sensibilité du dispositif expérimental** : fixation instrumentée vs maintien manuel, position axiale.

</td>
</tr>
</table>

<br>

<a id="p3b"></a>

<img src="assets/banners/p3b.png" width="100%" alt="B) Profil aéro pour l'injection de fumée en soufflerie">

> [!IMPORTANT]
> **🎯 Problématique et objectif** — Concevoir le profil aérodynamique d'un *smoke rake* pour réduire sa traînée parasite en soufflerie et assurer l'injection d'un flux de fumée non perturbé.

<p align="center">
<img src="https://img.shields.io/badge/1-S%C3%A9lection_du_profil-E0A800?style=flat-square" alt="1 · Sélection du profil"> ➜ <img src="https://img.shields.io/badge/2-Caract%C3%A9risation_du_sillage-E0A800?style=flat-square" alt="2 · Caractérisation du sillage"> ➜ <img src="https://img.shields.io/badge/3-Buses_et_impression_3D-E0A800?style=flat-square" alt="3 · Buses et impression 3D"> ➜ <img src="https://img.shields.io/badge/%E2%98%85-R%C3%A9trospective-555555?style=flat-square" alt="★ · Rétrospective">
</p>

#### <img src="https://img.shields.io/badge/%C3%89TAPE_1-Pr%C3%A9s%C3%A9lection_th%C3%A9orique_et_adaptation_CAO-E0A800?style=for-the-badge" alt="ÉTAPE 1 · Présélection théorique et adaptation CAO">

**⚙️ Action** — Sélection de 4 profils laminaires NACA série 6 symétriques (0 % de cambrure) à plus faible traînée, mis à l'échelle sous SolidWorks pour loger le smoke rake.

<p align="center">
<img src="assets/han/naca_63a010.png" width="70%"><br>
<sub><i>Exemple de profil retenu : 0 % de cambrure et faible traînée pour le Re de l'écoulement</i></sub>
</p>

#### <img src="https://img.shields.io/badge/%C3%89TAPE_2-Caract%C3%A9risation_CFD_en_sillage-E0A800?style=for-the-badge" alt="ÉTAPE 2 · Caractérisation CFD en sillage">

**⚙️ Action** — Simulations à V∞ = 22,2 m/s et extraction des vitesses sur une grille identique en aval pour comparer la perturbation de chaque profil.

<table>
<tr>
<td align="center" width="50%"><img src="assets/han/wake_18pct.png" width="100%"><br><sub>Profil 18 % d'épaisseur</sub></td>
<td align="center" width="50%"><img src="assets/han/wake_10pct.png" width="100%"><br><sub>Profil 10 % d'épaisseur ✅</sub></td>
</tr>
</table>

<p align="center"><sub><i>F1 le plus proche du bord de fuite, A6 le plus loin.</i></sub></p>

> [!TIP]
> **✅ Livrable** — Matrice de vitesses et choix du profil **10 % d'épaisseur**, dont les vitesses restent les plus proches de 22,2 m/s.

#### <img src="https://img.shields.io/badge/%C3%89TAPE_3-Optimisation_des_buses_et_conception_pour_impression_3D-E0A800?style=for-the-badge" alt="ÉTAPE 3 · Optimisation des buses et conception pour impression 3D">

**⚙️ Action** — Étude paramétrique CFD sur l'implantation des buses (en retrait, affleurantes ou sortantes) et comparaison des profils de vitesse en sillage pour retenir la géométrie offrant le flux le plus régulier.

<p align="center">
<img src="assets/han/nozzle_cutplot.png" width="80%"><br>
<sub><i>Cut plot comparatif : configuration de buse à perturbation minimale vs configuration défavorable</i></sub>
</p>

<p align="center">
<img src="assets/han/smoke_rake_print_1.png" height="260"> &nbsp;
<img src="assets/han/smoke_rake_print_2.png" height="260">
</p>

> [!TIP]
> **✅ Livrable** — Pièce imprimée en 3D ajustée sur le peigne, prête pour l'étape finale de lissage de surface avant les essais en soufflerie.

#### <img src="https://img.shields.io/badge/%E2%98%85-R%C3%A9trospective-555555?style=for-the-badge" alt="★ · Rétrospective">

<table>
<tr>
<th width="50%">💪 Compétences clés développées</th>
<th width="50%">🔧 Axes d'amélioration</th>
</tr>
<tr>
<td valign="top">

- **Dimensionnement aéro & CAO (SolidWorks)** : choisir un profil NACA et l'adapter sous contrainte d'encombrement.
- **Études paramétriques CFD** : comparer des champs de vitesse pour minimiser les perturbations.
- **Conception orientée intégration** : évider un volume intérieur, anticiper les jeux de montage.
- **Impression 3D (Cura)** : arbitrer entre finesse aérodynamique et contraintes d'impression.

</td>
<td valign="top">

- **Intégrer l'épaisseur requise en amont** : présélectionner sur la traînée réelle Fx après mise à l'échelle plutôt que sur un Cx catalogue.
- **Élargir les critères CFD** : perte de pression totale et énergie cinétique turbulente (TKE).
- **Validation expérimentale en soufflerie** après lissage pour corréler la CFD.

</td>
</tr>
</table>

<p align="right"><a href="#sommaire">⬆️ Retour au sommaire</a></p>

---

<div align="center">

📄 Portfolio complet : [`Portfolio_Cabaset_Nicolas.pdf`](Portfolio_Cabaset_Nicolas.pdf)

<sub>© Nicolas Cabaset</sub>

</div>
