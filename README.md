# Maroc_Explorer
MarocExplorer est un projet de prédiction géographique qui vise à estimer les coordonnées GPS (latitude, longitude) d’une image prise au Maroc, en exploitant à la fois son contenu visuel et les métadonnées associées à la ville correspondante (climat, architecture, altitude, type d’environnement, etc.).

L’approche consiste à utiliser une architecture inspirée de GeoNet (ex. : GeoGuessr, IM2GPS, PlaNet) pour extraire des représentations visuelles profondes via un modèle CNN (ResNet18 ...). Ces features sont ensuite combinées avec les caractéristiques de la ville dans une branche tabulaire, suivie d’un module de régression fully connected pour prédire les coordonnées GPS. Ce cadre permet de comparer objectivement les performances avec ou sans contexte urbain, afin de mieux comprendre l’influence des données complémentaires sur la précision géographique.

🎯 Destiné aux *chercheurs, **ingénieurs en vision par ordinateur* et *étudiants*, GeoVision met en lumière l’impact des données contextuelles sur la performance d’un modèle de régression géographique.

---

## 🚀 Objectifs Clés

* 🖼 *Prédire* les coordonnées GPS à partir d’images urbaines
* 🏙 *Comparer* les performances du modèle avec ou sans les caractéristiques des villes
* 🧠 *Combiner* une extraction d’images par CNN et un sous-réseau de caractéristiques tabulaires
* 📉 *Analyser* la précision des prédictions avec des métriques GPS pertinentes (MSE, Haversine, R²)

---

## 🔧 Pipeline Global

### 1. Chargement des données
Les données sont récupérées à partir d’un fichier contenant les métadonnées des images (noms, coordonnées GPS, ville associée), ainsi que les caractéristiques descriptives des villes. Les images sont organisées dans un dossier dédié.

### 2. Prétraitement
Un ensemble de transformations est appliqué pour préparer les données : traitement des variables numériques et catégorielles, ainsi que transformation des images pour les rendre exploitables par le modèle.

### 3. Modélisation
Le modèle extrait automatiquement les informations visuelles pertinentes à partir des images, et peut intégrer en complément des données tabulaires issues des villes. L’objectif est d’apprendre une fonction de régression permettant d’estimer la localisation géographique.

### 4. Entraînement
Le modèle est entraîné de manière supervisée sur les données annotées. Il est possible de tester l’impact des métadonnées des villes sur la précision en activant ou désactivant leur utilisation dans le pipeline.
---

## 📂 Arborescence du projet

bash
'''
MarocExplorer/
├── data/               # Données d'entraînement
│   ├── images/         # Dossier contenant les images urbaines
│   ├── coords.csv      # Coordonnées GPS des images (latitude, longitude, ville)
│   └── city_features.csv  # Caractéristiques des villes (climat, altitude, etc.)
│
├── model/              # Modèle
│   ├── modèle.pth      # Architecture du modèle
│
├── interface/          # Interface de visualisation ou démo
│   
├── notebooks/          # Analyses exploratoires ou tests en notebooks
│   └── MarocExplorer_Data.ipynb
│   └── MarocExplorer_Modèle.ipynb
│
└── README.md           # Présentation du projet
'''

