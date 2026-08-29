# MeNU+

Pipeline de détection d'anomalies comportementales pour drones (UAV) autonomes. L'approche combine un autoencodeur entraîné sur les vols normaux, un classifieur XGBoost optimisé par Optuna (avec SMOTE pour le déséquilibre de classes), et une agrégation temporelle par fenêtres glissantes à seuil adaptatif (mode Safety / mode Balanced).

Ce code accompagne le mémoire de maîtrise de Jean Frideland Delphin et l'article scientifique associé, en préparation pour soumission à *Discover Artificial Intelligence* (Springer Nature).

## Contenu

`MeNU_Plus_ALFA_public_version_finale.ipynb` contient l'ensemble du pipeline : chargement et nettoyage du dataset ALFA, sélection de variables, entraînement de l'autoencodeur, optimisation XGBoost, agrégation temporelle, ainsi que l'évaluation comparative face à dix approches de référence (Random Forest, régression logistique, LightGBM, etc.).

## Résultats (validation croisée GroupKFold, 5 folds)

| Approche | G-Mean | AUC-ROC |
|---|---|---|
| MeNU+ (autoencodeur + XGBoost + agrégation) | 0.8529 | 0.9057 |
| XGBoost + agrégation (sans autoencodeur) | 0.8502 | 0.9206 |
| Random Forest (features brutes) | 0.8441 | 0.9271 |
| LightGBM (features brutes) | 0.8367 | 0.9355 |

En mode opérationnel, deux seuils sont proposés : Safety Mode (recall maximisé, pour les vols critiques) et Balanced Mode (compromis précision/recall pour un usage standard).

## Dataset

Le pipeline est évalué sur ALFA (*A Dataset for UAV Fault and Anomaly Detection*), disponible sur KiltHub/CMU Figshare : https://doi.org/10.1184/R1/12707963

Le chemin d'accès au dataset se configure dans la section "Paramètres globaux" du notebook.

## Auteurs

Jean Frideland Delphin — Maîtrise en informatique (IA et cybersécurité), Université du Québec à Rimouski (UQAR)
Mehdi Adda — Département de mathématiques, informatique et génie, UQAR
