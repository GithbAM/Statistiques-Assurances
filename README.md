# Projet de Statistiques des Assurances

Projet de modélisation statistique réalisé dans le cadre du M2 ISEFAR (Ingénierie Statistique, Économique, Financière, Assurance et Risques) à l'Université Paris Nanterre.

## Présentation

Ce projet porte sur l'analyse et la modélisation d'une base de données d'assurance de **5352 observations** et **27 variables** socio-démographiques (PCS, catégories sociales, revenus, habitat, composition des ménages, etc.).

L'objectif est de développer des modèles statistiques robustes pour la tarification et l'analyse de risques en assurance, en utilisant des méthodes avancées de régression, d'analyse de survie et de traitement de données censurées.

## Objectifs

1. **Tarification a priori** : Modélisation GLM/GAM pour prédiction des sinistres
2. **Tarification a posteriori** : Tests d'endogénéité et modèles adaptatifs
3. **Données censurées** : Traitement de données avec forte proportion de zéros (76.3%)
4. **Nombre d'événements** : Modélisation du nombre de sinistres avec surdispersion
5. **Analyse de survie** : Identification des facteurs de risque par modèles de Kaplan-Meier et Cox

## Contenu du repository

- **`Projet_Assurance.pdf`** : Rapport complet (28 pages) avec analyse détaillée, méthodologie, résultats et interprétations
- **`Code_Annexe_Stats_des_Assusrances_ALBERI_Markus.pdf`** : Code R commenté (56 pages) avec toutes les analyses réalisées

## Méthodologies utilisées

### Analyses descriptives
- Analyses multivariées des variables socio-démographiques
- Stratification par âge, sexe, région, type d'habitat
- Tests statistiques pour identification de patterns

### Modélisation GLM/GAM
- **GLM Gamma** (link log) pour tarification a priori : R² = 0.75
- **GAM** avec splines pour relations non-linéaires
- Validation rigoureuse : Shapiro-Wilk, Breusch-Pagan, Cameron-Trivedi, Durbin-Watson, VIF
- Tests d'endogénéité : Wu-Hausman (p = 0.413)

### Données censurées
- **Modèle Tobit** : log-likelihood = -7100.5
- **Tobit Généralisé** : log-likelihood = -5166.5
- **Double Hurdle** (retenu) : log-likelihood = -5152.6

### Nombre d'événements
- **Poisson** : surdispersion détectée (dispersion = 2.89)
- **Binomiale Négative** (retenue) : theta = 2.03, AIC = 25972

### Analyse de survie
- **Kaplan-Meier** stratifiés par variables socio-démographiques
- **Tests du log-rank** : type habitat (p = 0.005), possession véhicule (p < 2e-16), âge (p < 2e-16)
- **Modèle de Cox** : C-index = 0.769

## Stack technique

**Langage** : R

**Packages principaux** :
- `survival` : Analyse de survie (Kaplan-Meier, Cox)
- `lmtest` : Tests statistiques (Breusch-Pagan, etc.)
- `car` : Tests de diagnostic (VIF, etc.)
- `MASS` : Régression Binomiale Négative
- `pscl` : Modèles pour données de comptage
- `mhurdle` : Modèles Double Hurdle
- `censReg` : Modèles Tobit

## Résultats principaux

- **R² = 0.75** pour le modèle GLM Gamma de tarification a priori
- **76.3% de zéros** dans les données de sinistres, traités avec succès par modèle Double Hurdle
- **Surdispersion significative** (2.89) dans le nombre de sinistres, corrigée par régression Binomiale Négative
- **C-index = 0.769** pour le modèle de Cox, indiquant une bonne capacité prédictive
- Identification de **facteurs de risque significatifs** : nombre d'adultes, catégories d'âge, type d'habitat, possession de véhicule

## Compétences démontrées

- Modélisation statistique avancée (GLM, GAM, Survie)
- Validation méthodologique rigoureuse
- Traitement de données complexes (censurées, surdispersion)
- Analyses multivariées et stratifiées
- Identification de facteurs de risque
- Rédaction scientifique détaillée
