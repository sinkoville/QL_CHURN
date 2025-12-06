# MODEL CARD – Prediction Churn

## 1. Objectif du modèle
Le modèle Prediction Churn vise à prédire la probabilité qu’un client résilie son abonnement. Il s’agit d’un problème de classification binaire destiné à la démonstration de bonnes pratiques ML.

## 2. Description du dataset
Dataset synthétique de 5 000 clients, généré dans Google Colab avec variables démographiques, financières, contractuelles et support client. Aucun NA, distributions contrôlées. Limites : données générées au hasard, certaines corrélations imposées.

## 3. Modèles entraînés
### Logistic Regression (baseline)
Interprétable, sert de référence.

### Random Forest (modèle principal)
Plus robuste et performant, capable de capturer des relations non linéaires.

## 4. Pipeline de préparation
- StandardScaler pour variables numériques  
- OneHotEncoder pour variables catégorielles  
- Pipeline scikit-learn assurant reproductibilité et absence de data leakage  

## 5. Évaluation du modèle
Métriques utilisées : Accuracy, Precision, Recall, F1-score, ROC-AUC.

### Importance :
Recall et ROC-AUC prioritaires dans le contexte du churn.

## 6. Explicabilité
Feature importance disponible pour Random Forest. Variables les plus influentes : tenure_months, contract_type, monthly_charge, support_calls.

## 7. Limitations du modèle
- Dataset synthétique → non valide pour production réelle  
- Pas de données temporelles  
- Fairness partielle (analyse par sous-groupes limitée)  
- Modèle non testé sous drift réel  

## 8. Risques éthiques & biais
- Sur-représentation de certaines catégories (contrats, régions)  
- Risque de discrimination involontaire  
- Biais reproduits par le modèle si présents dans les données  

Mitigation : analyse par sous-groupes, ajustements de seuils, rééquilibrage.



## 9. Perspectives d’amélioration
- Ajouter des données réelles ou semi-synthétiques  
- Tester XGBoost/LightGBM  
- Hyperparameter tuning complet  
- Intégration MLflow pour tracking  
- Tests unitaires ML  
- Monitoring du drift  

## 10. Fichiers associés
- logistic_regression_model.pkl  
- random_forest_model.pkl  
- synthetic_churn_dataset.csv  

