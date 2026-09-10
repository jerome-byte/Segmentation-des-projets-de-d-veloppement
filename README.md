# Segmentation des Projets de Développement Clustering & Machine Learning Non Supervisé

Projet d'analyse de données et de clustering appliqué au portefeuille de projets de développement d'une institution financière régionale ouest-africaine (contexte inspiré de la BOAD / UEMOA).

>  **Note sur les données**  ce projet utilise un jeu de données **synthétique** (200 projets générés de manière réaliste), créé à des fins de démonstration pédagogique. Aucune donnée réelle de la BOAD n'a été utilisée.

## Objectif

Segmenter un portefeuille de 200 projets de développement (couvrant 8 pays et 8 secteurs de l'UEMOA) en groupes homogènes, afin de faciliter :
- le pilotage et le suivi différencié des projets,
- l'identification de profils de risque,
- l'aide à la décision pour l'allocation des ressources.

## Contenu du dépôt

```
├── segmentation_projets.ipynb   # Notebook principal (analyse complète)
├── donnees_segmentation.csv     # Jeu de données généré (si présent)
├── figures/                     # Graphiques exportés (22 figures, .png)
└── README.md
```

## Méthodologie

Le notebook suit un pipeline complet de data science, en 11 étapes :

1. **Contexte & objectifs**  cadrage métier du projet
2. **Génération du jeu de données synthétique** 200 projets réalistes (montant, durée, bénéficiaires, emplois créés, impact environnemental, score de risque, avancement…)
3. **Analyse exploratoire (EDA)** distributions par pays/secteur, corrélations, relations montant/bénéficiaires/risque
4. **Prétraitement** standardisation des variables (`StandardScaler`) indispensable avant clustering
5. **Choix du nombre optimal de clusters** méthode du coude (Elbow Method) **et** score de silhouette, utilisés conjointement
6. **Modélisation K-Means** (k = 4) entraînement, visualisation par ACP (PCA) en 2D
7. **Profilage des clusters** caractérisation statistique et métier de chaque segment (radar chart, boxplots)
8. **Clustering hiérarchique ascendant** (Agglomerative Clustering, méthode de Ward) dendrogramme et comparaison avec K-Means
9. **Interprétation métier & recommandations** nommage et description des 4 profils de projets identifiés

## Résultats principaux

- **k = 4** clusters retenus (convergence entre méthode du coude et score de silhouette)
- Score de silhouette moyen ≈ **0,28** : indique une structure de clusters modérée, cohérente avec le chevauchement naturel des profils de projets de développement
- **4 profils identifiés** :
  - Projets d'infrastructure de transport (fort impact emploi)
  - Petits projets à faible risque (secteur éducation dominant)
  -  Grands projets d'infrastructure
     Projets sociaux à fort impact
- Les résultats du K-Means et du clustering hiérarchique sont globalement concordants, ce qui renforce la robustesse de la segmentation

##  Stack technique

- **Python 3**
- `pandas`, `numpy` 
- `matplotlib`, `seaborn` 
- `scikit-learn` `StandardScaler`, `KMeans`, `AgglomerativeClustering`, `PCA`, `silhouette_score`
- `scipy`  `linkage`, `dendrogram`

## Reproduire le projet

```bash
# Cloner le dépôt
git clone <url-du-repo>
cd <repo>

# Installer les dépendances
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter

# Lancer le notebook
jupyter notebook segmentation_projets.ipynb
```

