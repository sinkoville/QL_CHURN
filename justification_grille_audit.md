# Justification théorique – Grille d’audit (Version courte)

La justification de cette grille s’appuie sur des recommandations issues des bonnes pratiques MLOps (Google, Microsoft TDSP), de la gestion de la qualité des données (ISO/IEC 25012) et de standards modernes de validation des modèles (Model Cards Framework).

---

## 1. Qualité des données – Justification

### ✔ Complétude  
L’absence de valeurs manquantes est essentielle car elle garantit que le modèle apprend sur des données complètes et fiables. Des NA non traités dégradent directement la performance.

### ✔ Cohérence interne  
Les données doivent respecter des contraintes logiques (ex : total_charge ≥ 0). Cela évite d’entraîner un modèle sur des cas impossibles ou contradictoires.

### ✔ Types corrects  
Des erreurs de types (string au lieu de float) créent des bugs dans les pipelines de preprocessing. Le contrôle des types est une exigence fondamentale en MLOps.

### ✔ Outliers et distributions  
Les valeurs extrêmes peuvent biaiser les modèles, particulièrement les modèles linéaires. Leur analyse permet de stabiliser l’apprentissage.

### ✔ Biais potentiels  
Un dataset déséquilibré peut créer un modèle discriminatoire. L'identification des biais potentiels est recommandée par les guides "Responsible AI".

### ✔ Stabilité (data drift)  
Comparer train/test permet de s’assurer que les distributions ne changent pas brutalement. C’est un principe du monitoring en production.

### ✔ Pertinence métier  
Les features doivent être pertinentes pour expliquer le churn. Une variable sans lien métier dégrade inutilement le modèle.

---

## 2. Qualité du modèle – Justification

### ✔ Pertinence des métriques  
En churn, on privilégie Recall et ROC-AUC car l’objectif est d’identifier un maximum de clients à risque. Une mauvaise métrique fausse l’évaluation du modèle.

### ✔ Robustesse  
Un modèle fiable doit donner des résultats stables même si les données changent légèrement. Cela réduit les risques en production.

### ✔ Stress-tests  
Les stress-tests permettent de vérifier la résistance du modèle à des scénarios inhabituels (colonnes manquantes, bruit, variations). Bonne pratique recommandée dans le MLOps Lifecycle.

### ✔ Fairness / biais  
Tester les performances par sous-groupes (ex : régions, type de contrat) réduit le risque de discrimination.

### ✔ Explicabilité  
Indispensable pour comprendre comment le modèle prend ses décisions et faciliter la validation métier. Recommandé par Google AI Explainability.

---

## 3. Qualité du code & reproductibilité – Justification

### ✔ Modularité  
Du code modulaire facilite la maintenance et permet de réutiliser les composants (data prep, training, evaluation).

### ✔ Versioning Git  
Git garantit la traçabilité des versions de code, essentielle dans un projet ML professionnel.

### ✔ Reproductibilité (seeds)  
Fixer les seeds assure des résultats identiques d’une exécution à l’autre, ce qui est essentiel pour l’audit.

### ✔ Requirements  
Lister les dépendances évite les erreurs d’environnement lors de l’exécution du projet.

### ✔ Sauvegarde des modèles  
Permet de versionner les modèles entraînés et facilite l’industrialisation.

---

## 4. Qualité documentaire – Justification

### ✔ README  
Document indispensable pour permettre à toute personne d’exécuter et comprendre le projet.

### ✔ Model Card  
Standard moderne pour documenter :  
- objectif du modèle  
- limites  
- risques  
- biais  
- conditions d’usage  

### ✔ Documentation du code  
Facilite la compréhension et la maintenance.
