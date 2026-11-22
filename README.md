# CodeAlpha — Data Science Internship

Projets réalisés dans le cadre du stage **Data Science** chez [CodeAlpha](https://www.codealpha.tech) : trois tâches de bout en bout (chargement, nettoyage, exploration, visualisation, modélisation, évaluation) avec Python.

**Auteur :** Hayat
**Vidéo de présentation (LinkedIn) :** <!-- colle ici le lien de ta vidéo -->

---

## Les trois projets

| # | Projet | Type | Dossier | Notebook |
|---|--------|------|---------|----------|
| 1 | Classification des fleurs Iris | Classification | `CodeAlpha_IrisClassification/` | `Iris_classification.ipynb` |
| 2 | Analyse du chômage en Inde (impact Covid-19) | Analyse de données | `CodeAlpha_unemployment_analysis/` | `Unemployment_analysis.ipynb` |
| 3 | Prédiction du prix des voitures | Régression | `CodeAlpha_CarPricesPrediction/` | `car_prices_prediction.ipynb` |

---

## Tâche 1 — Classification des fleurs Iris

**Objectif :** prédire l'espèce d'une fleur (*setosa*, *versicolor*, *virginica*) à partir de 4 mesures : longueur et largeur des sépales et des pétales.

**Données :** dataset Iris intégré à scikit-learn (150 fleurs, 3 espèces équilibrées, aucun fichier à télécharger).

**Démarche**
1. Exploration : valeurs manquantes, doublons, équilibre des classes.
2. Visualisation : `pairplot`, boîtes à moustaches, corrélations.
3. Découpage 80 % entraînement / 20 % test (stratifié).
4. Comparaison de 4 modèles : KNN, régression logistique, arbre de décision, Random Forest, avec validation croisée à 5 plis.
5. Évaluation du meilleur modèle : accuracy, rapport de classification, matrice de confusion.

**Résultats**

| Modèle retenu | Accuracy (jeu de test) |
|---------------|------------------------|
| <!-- ex. KNN --> | <!-- ex. 93 % --> |

**À retenir :** les mesures des pétales séparent très bien les espèces. *Setosa* est parfaitement reconnue ; les rares erreurs concernent *versicolor* et *virginica*, qui se ressemblent.

---

## Tâche 2 — Analyse du chômage en Inde (impact de la Covid-19)

**Objectif :** nettoyer, explorer et visualiser les taux de chômage, mesurer l'impact de la Covid-19 et en tirer des recommandations de politiques économiques et sociales.

**Données (2 fichiers complémentaires)**

| Fichier | Période | Contenu |
|---------|---------|---------|
| `Unemployment in India.csv` | mai 2019 → juin 2020 | 28 régions, séparées en Rural / Urbain |
| `Unemployment_Rate_upto_11_2020.csv` | jan 2020 → oct 2020 | 27 États, zone géographique, coordonnées GPS |

**Démarche**
- Nettoyage : espaces parasites dans les colonnes et les valeurs, lignes vides, BOM, dates au format jour-mois-année, colonnes GPS inversées dans le second fichier.
- Comparaison avant / pendant / après le confinement (national, par État, par zone).
- Comparaison zones rurales et urbaines, carte du choc par État.
- Lien entre chômage, emploi et participation au marché du travail.

**Résultats clés** (moyennes simples sur les États)
- Le chômage passe de **9,2 %** (jan-fév 2020) à **environ 23 %** en avril-mai 2020 (x2,5), avec un pic à **23,2 % en mai**, puis retombe à **8,0 %** en octobre.
- Avant la crise, le chômage urbain est plus élevé que le rural (**10,8 %** contre **8,1 %**) ; les deux explosent pendant le confinement.

## Tâche 3 — Prédiction du prix des voitures

**Objectif :** entraîner un modèle de régression qui prédit le prix d'une voiture à partir de ses caractéristiques.

**Données :** car data.csv (variable cible Selling_Price) : année, prix neuf, kilométrage, carburant, type de vendeur, boîte de vitesses, nombre de propriétaires.

**Démarche**

- Nettoyage (doublons) et création de la variable âge du véhicule à partir de l'année.
- Exploration : distribution du prix, corrélations, prix selon les variables catégorielles.
- Prétraitement dans un Pipeline : mise à l'échelle des variables numériques, encodage one-hot des catégories (appris sur l'entraînement uniquement, pour éviter toute fuite vers le test).
- Comparaison de 4 modèles : régression linéaire, Ridge, Random Forest, Gradient Boosting (validation croisée à 5 plis).
- Évaluation : R², MAE, RMSE, graphiques prix réel vs prédit et résidus, importance des variables.

**Résultats**

Modèle retenu	R² (test)	MAE (test)
<!-- ex. Random Forest -->	<!-- ex. 0.95 -->	<!-- ex. 0.6 -->

**Limites :** dataset de taille modeste, donc les scores varient selon le découpage train/test.

**Structure du dépôt**
.
├── CodeAlpha_IrisClassification/
│   └── Iris_classification.ipynb
├── CodeAlpha_unemployment_analysis/
│   └── Unemployment_analysis.ipynb
├── CodeAlpha_CarPricesPrediction/
│   └── car_prices_prediction.ipynb
├── requirements.txt
└── README.md

**Données**

Les fichiers CSV ne sont pas inclus dans ce dépôt. Pour relancer les notebooks, téléchargez les jeux de données fournis par CodeAlpha dans les consignes du stage et placez-les dans le dossier de leur projet :

|Dossier	                       | Fichier(s) attendu(s)|
|----------------------------------|
|CodeAlpha_IrisClassification/	   | aucun (données intégrées à scikit-learn)|
|CodeAlpha_unemployment_analysis/  | Unemployment in India.csv et Unemployment_Rate_upto_11_2020.csv|
|CodeAlpha_CarPricesPrediction/	   | car data.csv|

**Installation et exécution**
1. Créer et activer un environnement virtuel
python -m venv venv
venv\Scripts\activate          # Windows

source venv/bin/activate     # macOS / Linux

2. Installer les dépendances
pip install -r requirements.txt

3. Lancer Jupyter
jupyter notebook


Puis ouvrir le notebook du projet voulu et l'exécuter de haut en bas.

**Technologies**

Python · pandas · NumPy · matplotlib · seaborn · scikit-learn · Jupyter