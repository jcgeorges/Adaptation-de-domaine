# Adaptation de domaine : étude théorique et illustration expérimentale

**Projet de Travail d'Étude et de Recherche (TER) — Master 1 Data Science**

## Présentation du projet

L'adaptation de domaine (*Domain Adaptation*) est un problème d'apprentissage automatique qui consiste à transférer les connaissances acquises à partir d'un domaine source vers un domaine cible, lorsque les distributions des données diffèrent entre ces deux domaines.

En pratique, un modèle entraîné sur un ensemble de données peut perdre en performance lorsqu'il est appliqué à des données provenant d'un environnement différent. L'adaptation de domaine cherche à comprendre les conditions dans lesquelles un modèle peut conserver de bonnes performances malgré ces différences.

Ce projet porte sur l'étude théorique de l'adaptation de domaine pour la classification binaire. Il s'appuie sur les travaux de Ben-David et de ses collaborateurs concernant les fondements théoriques de l'apprentissage à partir de domaines différents.

Le travail comprend l'étude des définitions, l'analyse et la démonstration de résultats théoriques, ainsi que la construction d'un exemple synthétique en Python pour illustrer les principaux concepts.

## Objectifs

Les principaux objectifs du projet sont :

- Comprendre le problème de l'adaptation de domaine et ses fondements mathématiques.
- Étudier les relations entre l'erreur de classification dans les domaines source et cible.
- Analyser le rôle de la divergence entre les distributions dans la généralisation des modèles.
- Comprendre la H-divergence et ses propriétés.
- Étudier la divergence symétrique HΔH et son rôle dans l'analyse des erreurs de classification.
- Comprendre les conditions théoriques favorisant une bonne adaptation entre deux domaines.
- Illustrer les concepts étudiés à travers une simulation numérique et des visualisations en Python.

## Contenu de l'étude théorique

### 1. Formalisation de l'adaptation de domaine

Le problème est étudié dans le cadre de la classification binaire.

Deux domaines sont considérés :

- **Domaine source** : domaine à partir duquel le modèle apprend.
- **Domaine cible** : domaine sur lequel on souhaite obtenir de bonnes performances.

L'étude porte notamment sur les différences entre les distributions des observations et entre les fonctions d'étiquetage des deux domaines.

### 2. Théorème 1 : relation entre l'erreur source et l'erreur cible

Le premier théorème établit une borne théorique sur l'erreur de classification dans le domaine cible.

Cette borne dépend de trois éléments principaux :

- L'erreur du classificateur dans le domaine source.
- La divergence entre les distributions source et cible.
- Le désaccord entre les fonctions d'étiquetage des deux domaines.

Ce résultat permet de comprendre pourquoi une faible erreur sur les données d'entraînement ne garantit pas nécessairement de bonnes performances sur un domaine différent.

L'étude met également en évidence les limites de la divergence L1 pour mesurer les différences entre distributions à partir d'échantillons finis.

### 3. H-divergence

La H-divergence est introduite pour mesurer les différences entre deux distributions en tenant compte d'une classe d'hypothèses donnée.

Contrairement à une mesure générale de divergence, elle se concentre sur les différences que les hypothèses de cette classe peuvent détecter.

Cette partie étudie sa définition, son interprétation et la possibilité de l'estimer à partir d'échantillons non étiquetés.

Elle présente également le principe consistant à entraîner un classificateur pour distinguer les observations provenant du domaine source de celles provenant du domaine cible.

### 4. Hypothèse jointe idéale

L'hypothèse jointe idéale est celle qui minimise la somme des erreurs de classification dans les domaines source et cible.

Son rôle est essentiel pour comprendre les limites de l'adaptation de domaine.

Si aucune hypothèse de la classe étudiée ne permet de bien classifier les observations des deux domaines, une bonne adaptation ne peut pas être garantie par le seul apprentissage sur le domaine source.

### 5. Divergence symétrique HΔH

La divergence symétrique HΔH s'appuie sur les désaccords entre les hypothèses d'une même classe.

Elle permet de mesurer les différences entre domaines à travers les régions de l'espace où des classificateurs peuvent produire des prédictions différentes.

Cette notion joue un rôle central dans l'établissement d'une borne plus adaptée à l'étude de l'erreur cible.

### 6. Théorème 2 : borne de généralisation dans le domaine cible

Le deuxième théorème fournit une borne sur l'erreur cible faisant intervenir :

- L'erreur du classificateur dans le domaine source.
- La divergence empirique HΔH entre les domaines.
- Un terme statistique dépendant de la taille des échantillons, de la dimension VC et du niveau de confiance.
- L'erreur combinée de l'hypothèse jointe idéale.

L'utilisation de la divergence empirique permet de relier les résultats théoriques à des quantités estimables à partir de données non étiquetées.

Ce résultat met en évidence l'importance conjointe de la performance sur le domaine source, du décalage entre les domaines et de la compatibilité des deux tâches de classification.

## Exemple synthétique en Python

Afin d'illustrer les concepts théoriques, un exemple synthétique est construit en dimension deux.

### Construction du domaine source

Les observations du domaine source sont générées à partir d'un mélange équilibré de deux distributions gaussiennes.

Les étiquettes sont ensuite générées à partir d'une fonction de score transformée en probabilités à l'aide d'une fonction sigmoïde. Un mécanisme probabiliste permet d'introduire du bruit dans les étiquettes observées.

### Construction du domaine cible

Le domaine cible est construit à partir de nouvelles observations issues de la même procédure de génération initiale, auxquelles est appliquée une transformation géométrique comprenant :

- Un changement d'échelle.
- Une rotation.
- Une translation.

La fonction utilisée pour générer les étiquettes est également modifiée afin d'introduire une différence entre les mécanismes d'étiquetage des deux domaines.

Cette construction permet d'étudier séparément le décalage entre les distributions des observations et le désaccord entre les fonctions d'étiquetage.

### Visualisation des domaines

Trois graphiques illustrent l'exemple :

- **Figure 1 — Domaine source :** distribution des observations et répartition des classes.
- **Figure 2 — Domaine cible :** distribution des observations après transformation et répartition des classes.
- **Figure 3 — Comparaison des domaines :** superposition des observations source et cible pour visualiser leur décalage géométrique.

Ces visualisations facilitent l'interprétation des notions étudiées dans les théorèmes. Elles illustrent le décalage de domaine, sans constituer à elles seules une vérification expérimentale complète des bornes théoriques.

## Technologies utilisées

- **Python** : génération des données et réalisation des expériences.
- **NumPy** : calcul numérique, génération des observations et transformations géométriques.
- **Matplotlib** : visualisation et comparaison des domaines.
- **scikit-learn** : outils de classification et d'expérimentation, selon les scripts utilisés.
- **LaTeX** : rédaction du rapport scientifique.
- **Beamer** : préparation de la présentation.

## Organisation du dépôt

Le dépôt contient les documents associés au projet :

- `rapport.pdf` : version PDF du rapport.
- `main.tex` : source LaTeX du rapport.
- `presentation.pdf` : version PDF de la présentation.
- `presentation.tex` : source LaTeX de la présentation.
- `figures/` : graphiques utilisés pour illustrer l'exemple synthétique.

Les noms et les chemins doivent correspondre aux fichiers réellement présents dans le dépôt.

## Compétences mobilisées

Ce projet permet de mobiliser et de développer plusieurs compétences en Data Science :

- Lecture et analyse d'un article scientifique.
- Compréhension et formalisation mathématique de problèmes d'apprentissage automatique.
- Analyse et démonstration de théorèmes.
- Étude des distributions de probabilité et des mesures de divergence.
- Génération de données synthétiques avec Python.
- Visualisation et interprétation de données.
- Rédaction scientifique avec LaTeX.
- Mise en relation des résultats théoriques avec des exemples numériques.

## Référence scientifique

Ben-David, S., Blitzer, J., Crammer, K., Kulesza, A., Pereira, F. et Vaughan, J. W.

**A Theory of Learning from Different Domains.**

Ce travail s'inscrit dans le cadre théorique de l'adaptation de domaine développé par ces auteurs.

## Auteur

**Georges Jean Constantin**

Étudiant en Data Science — Université d'Angers

Projet de TER réalisé dans le cadre du cursus universitaire.

---

*Ce dépôt présente un travail universitaire consacré aux fondements théoriques de l'adaptation de domaine et à leur illustration par un exemple synthétique.*
