# Rapport Critique – Prediction Churn  
*(Version 4 pages)*

## 1. Introduction

Ce rapport présente un audit critique du projet *Prediction Churn*, réalisé dans le cadre du module Qualité du Livrable – MDSIA2025.  
L’objectif est de prédire la résiliation client (churn) au moyen d'un pipeline complet de Machine Learning, incluant gestion de la qualité des données, audit, documentation et outil avancé.

Le rapport met en avant :  
1) les points forts,  
2) les limites du livrable,  
3) les risques d'utilisation en production,  
4) les pistes d'amélioration envisageables.

---

## 2. Points forts du livrable

### 2.1 Qualité du dataset  
Le dataset synthétique a été généré de manière contrôlée, garantissant :  
- absence totale de valeurs manquantes,  
- cohérence interne (relations logiques respectées),  
- distributions réalistes,  
- logique métier intégrée dans la probabilité de churn.

Cela permet un entraînement propre et reproductible du modèle.

### 2.2 Robustesse de la modélisation  
Deux modèles ont été réalisés :  
- **Logistic Regression** (baseline),  
- **Random Forest** (modèle principal).  

Le pipeline scikit-learn assure une reproductibilité totale :  
- standardisation des variables numériques,  
- encodage des variables catégorielles,  
- pipeline unifié évitant le data leakage,  
- random_state fixé partout,  
- sauvegarde des modèles (pkl).

Les métriques choisies (Recall, F1, ROC-AUC) sont adaptées au churn, où identifier les clients à risque est prioritaire.

### 2.3 Démarche qualité intégrée  
Le projet inclut :  
- grille d’audit complète,  
- fichier pré-rempli d’auto-évaluation,  
- justification théorique,  
- Model Card,  
- README professionnel.  

Cette documentation démontre une bonne compréhension des standards MLOps et de la qualité ML.

### 2.4 Intégration d’un outil avancé : Great Expectations  
Great Expectations ajoute un contrôle qualité automatisé :  
- tests de distributions,  
- validation des types,  
- vérification de cohérence,  
- génération de rapports HTML.

---

## 3. Limites du livrable

### 3.1 Dataset synthétique  
Bien que propre, il ne reflète pas toutes les complexités réelles :  
- pas de données temporelles,  
- corrélations artificielles,  
- pas de dynamique concurrentielle ou saisonnalité.

### 3.2 Validation croisée absente  
Le modèle utilise un split simple train/test.  
Une validation croisée k-fold aurait permis une estimation plus robuste et réduit la variance.

### 3.3 Fairness à approfondir  
La grille inclut la fairness, mais l’analyse par sous-groupes (ex : région, type de contrat) n’a pas été réalisée.

### 3.4 Documentation perfectible  
La Model Card pourrait être enrichie avec :  
- les valeurs finales des métriques,  
- un schéma d’architecture,  
- plus de détails sur l’explicabilité.

---

## 4. Risques en production

### 4.1 Data Drift  
Les comportements clients évoluent. Sans monitoring, les performances du modèle se dégraderont.

### 4.2 Biais et discrimination  
Des déséquilibres dans les catégories du dataset peuvent induire des biais de décision.

### 4.3 Risques métier  
Un modèle imprécis peut provoquer :  
- des dépenses marketing inutiles,  
- un manque de réactions envers les vrais churners,  
- une perte de confiance interne.

### 4.4 Interprétabilité limitée  
Le Random Forest, performant mais non interprétable par défaut, demanderait SHAP/LIME pour être vraiment transparent.

---

## 5. Pistes d'amélioration

### 5.1 Enrichissement du dataset  
- Ajouter variables comportementales et historiques.  
- Introduire des données temporelles.  
- Fusionner avec des données externes (concurrence, pricing).

### 5.2 Amélioration des modèles  
- Hyperparameter tuning complet.  
- Test de modèles avancés (XGBoost, LightGBM, CatBoost).  
- Ajout d’explicabilité (SHAP, PDP).

### 5.3 Renforcement MLOps  
- Tracking MLflow pour retracer : dataset, modèles, paramètres, métriques.  
- Tests unitaires ML (pytest).  
- Monitoring de drift.

### 5.4 Approfondir les audits  
- Analyse fairness complète par sous-groupes.  
- Stress-tests supplémentaires : bruit, colonnes manquantes, permutations.  
- Calibration des seuils pour maximiser Recall ou F1 selon le besoin métier.

---

## 6. Conclusion

Le projet *Prediction Churn* constitue un livrable solide, intégrant pipeline, modélisation reproductible, audit structuré, documentation professionnelle et contrôle qualité automatisé.  
Ses limites sont principalement liées au dataset synthétique et à l’absence de validation/fairness avancées.  

Ce travail constitue toutefois une base robuste pour évoluer vers un projet MLOps réellement industrialisable.

