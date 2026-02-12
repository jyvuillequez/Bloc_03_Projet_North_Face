# Bloc 03 – Projet North Face

Analyse de données retail pour comprendre les comportements d’achat et améliorer la segmentation client et les recommandations produits.

Projet réalisé dans le cadre de la certification **RNCP Niveau 6 – Concepteur Développeur en Science des données (Jedha Bootcamp)**.

## 1. Contexte & enjeux

- **Problématique métier :** Le catalogue e-commerce de The North Face repose sur des descriptions produits textuelles riches mais hétérogènes. En l’absence de labels structurés ou de données utilisateurs exploitables, l’enjeu est  d’améliorer la structuration du catalogue et les recommandations produits.
- **Décideurs cibles :** marketing, produit

## 2. Objectifs du projet

- Analyse exploratoire de données (EDA)
- Préparation et nettoyage de données textuelles
- NLP : vectorisation TF-IDF
- Machine Learning non supervisé (KMeans, DBSCAN, LSA)
- Visualisation et interprétation des résultats

## 3. Compétences mobilisées

- Analyse exploratoire de données (EDA)
- Préparation et nettoyage de données
- Modélisation / Machine Learning (si applicable)
- Visualisation et restitution
- Recommandations orientées Buisiness

## 4. Données

- **Source :** Catalogue produits The North Face (descriptions textuelles)

- **Périmètre :** Environ 500 produits, chacun décrit par un texte libre

- **Variables clés :**
  - `id` : identifiant produit  
  - `description` : description textuelle brute  
  - `clean` : texte nettoyé  
  - `kmeans_cluster` : cluster attribué par KMeans  
  - `main_topic` : topic dominant issu du LSA  

## 5. Méthodologie

1. **Préparation des données**
   - Suppression des balises HTML
   - Normalisation du texte (lowercase, nettoyage des caractères)
   - Analyse des lemmes les plus fréquents

2. **Représentation sémantique**
   - Vectorisation des descriptions via **TF-IDF**
   - Création d’une matrice sémantique produit × termes

3. **Clustering non supervisé**
   - DBSCAN (cosine) pour l’analyse exploratoire des familles naturelles
   - KMeans pour une structuration exhaustive du catalogue
   - Sélection de **K = 15** comme compromis entre performance et interprétabilité

4. **Système de recommandation**
   - Recommandation basée sur l’appartenance à un même cluster KMeans
   - Implémentation simple (“same cluster”)

5. **Topic Modeling**
   - Extraction de thèmes latents via **LSA (TruncatedSVD)**
   - Identification des topics dominants et analyse de leur distribution

## 6. Résultats & recommandations

- Le clustering KMeans permet de structurer le catalogue en 15 clusters sémantiquement cohérents
- Les clusters reflètent des thématiques claires (matières, propriétés techniques, usages)
- Le système de recommandation propose des produits similaires de manière simple
- Le topic modeling met en évidence des dimensions transverses (durabilité, imperméabilité, matières)

### Recommandation business
Utiliser les clusters pour alimenter les sections *“You may also like”* et les topics pour enrichir les filtres et la navigation.

## 7. Installations des librairies Python
```text
python -m pip install -r requirements.txt
```

## 8. Organisation du projet

```text
.
├─ data/
│  ├─ raw/        # données brutes
│  └─ outputs/    # exports csv (clusters, topics)
├─ notebooks/     # notebooks Jupyter (EDA, clustering, LSA)
├─ src/           # scripts Python (recommender.py, utils)
└─ presentation/  # slides de restitution
