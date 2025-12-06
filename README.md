# QL_CHURN
Evaluation Finale Qualité du livrable  
Ce projet a été réalisé dans le cadre du module Qualité du Livrable – MDSIA2025.  
L’objectif est de construire un mini-projet complet de machine learning permettant de prédire le churn client (résiliation) à partir d’un dataset synthétique généré pour l’étude.

Le projet intègre :  \
✔ un dataset propre  
✔ un pipeline ML robuste  
✔ un modèle baseline + modèle performant  
✔ des métriques complètes  
✔ une grille d’audit qualité  
✔ un auto-audit critique  
✔ un outil avancé de qualité : Great Expectations  

# 2. Dataset

Le dataset a été généré afin de reproduire un contexte réaliste de churn dans le secteur des telecoms.
Il comporte 5 000 clients et les variables suivantes :

âge, ancienneté (mois), type de contrat, prix mensuel,total payé, appels au support, type d’accès internet, méthode de paiement, promotion active, région, churn (cible : 0 = reste, 1 = résilie)

✔ Particularités du dataset
Aucun NA
Distributions contrôlées
Cohérence interne vérifiée
Logique métier intégrée dans la probabilité de churn

# 3. Modèles utilisés
Deux modèles ont été entraînés :
1. Logistic Regression (baseline)
Interprétable
Créée pour fournir un point de référence
2. Random Forest (modèle principal)
Plus performant
Capable de capturer les non-linéarités
Feature importance interprétable
Les deux modèles sont intégrés dans un pipeline scikit-learn incluant :
Standardisation des variables numériques

Encodage One-Hot des variables catégorielles
Entraînement du modèle
Sauvegarde automatisée

# 4. Évaluation du Modèle
Les métriques utilisées sont :
Accuracy
Precision
Recall
F1-score
ROC-AUC
Matrice de confusion
✔ Raisons du choix
Le churn est un problème où le Recall et le ROC-AUC sont essentiels :
→ identifier un client à risque est plus critique que les faux positifs.

# 5. Justification méthodologique

Le dataset synthétique permet de contrôler la logique métier du churn.
La baseline Logistic Regression offre une référence simple et interprétable.
Le Random Forest est un modèle standard robuste pour les données tabulaires.
Le pipeline assure la reproductibilité et évite les fuites de données (data leakage).
Les métriques choisies répondent aux contraintes d’un problème business réel.

La justification détaillée est disponible dans la Model Card.

# 6. Outil avancé de qualité : Great Expectations

Great Expectations a été intégré pour :

vérifier la complétude

valider les distributions

garantir la cohérence interne

détecter tout drift ou anomalie

Les tests couvrent :

valeurs min/max

types attendus

cardinalité de colonnes catégorielles

seuil d’acceptable pour les valeurs manquantes

cohérence tenure → total_charge
 Model Card : [Consulter ici](model_card.md)
