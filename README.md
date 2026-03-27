# Analyse du risque de maladie cardiaque

Projet de portfolio data analyst centré sur l’exploration de données médicales et la construction d’un modèle de classification simple, interprétable et orienté métier.

## Objectif

L’objectif de ce projet est d’identifier les facteurs les plus associés à la présence d’une maladie cardiaque et de construire un modèle capable d’aider à la détection des patients à risque.

Dans une logique métier, l’enjeu principal est de **limiter les faux négatifs**, c’est-à-dire éviter de ne pas détecter un patient réellement à risque.

## Problématique métier

Dans un contexte de dépistage, toutes les erreurs n’ont pas le même coût :

- un **faux négatif** peut retarder la prise en charge d’un patient à risque ;
- un **faux positif** peut conduire à des examens complémentaires inutiles, mais reste généralement moins critique.

Le projet cherche donc à construire une approche **simple, lisible et exploitable**, plutôt qu’un modèle complexe difficile à interpréter.

## Jeu de données

Le projet repose sur un jeu de données cliniques contenant des variables comme :

- l’âge ;
- la pression artérielle ;
- le cholestérol ;
- la fréquence cardiaque maximale ;
- la dépression du segment ST ;
- différents indicateurs cliniques catégoriels.

La variable cible correspond à la **présence ou l’absence de maladie cardiaque**.

## Démarche analytique

Le projet a été structuré en plusieurs étapes :

1. **Compréhension du besoin métier**
2. **Audit qualité des données**
3. **Analyse exploratoire des variables numériques et catégorielles**
4. **Analyse des relations avec la cible**
5. **Prétraitement des données**
   - standardisation des variables numériques ;
   - encodage des variables catégorielles ;
6. **Modélisation avec une régression logistique**
7. **Validation croisée**
8. **Évaluation finale sur jeu de test**
9. **Analyse du seuil de décision**
10. **Interprétation des coefficients**

## Principaux enseignements de l’EDA

L’analyse exploratoire met en évidence plusieurs signaux utiles pour la détection du risque cardiaque.

### Variables numériques les plus informatives
- **ST depression** apparaît comme l’un des signaux les plus marqués ;
- **Max HR** montre une relation inverse avec la présence de maladie cardiaque ;
- **Age** semble également jouer un rôle ;
- **BP** et **Cholesterol** paraissent moins discriminants pris isolément.

### Variables catégorielles les plus discriminantes
Les écarts les plus visibles concernent notamment :

- **Chest pain type**
- **Exercise angina**
- **Slope of ST**
- **Number of vessels fluro**
- **Thallium**

## Modèle retenu

Le projet repose sur une **régression logistique**.

Ce choix a été fait pour trois raisons principales :

- **interprétabilité** ;
- **simplicité de mise en œuvre** ;
- **cohérence avec un usage d’aide à la décision**.

L’objectif n’était pas de maximiser la complexité technique, mais de proposer un modèle compréhensible par des profils non techniques.

## Résultats

### Validation croisée
La validation croisée montre des performances globalement solides et relativement stables :

- **Accuracy** : 0.833
- **Precision** : 0.829
- **Recall** : 0.792
- **F1-score** : 0.808
- **ROC AUC** : 0.907

### Jeu de test
Les performances observées sur le jeu de test confirment la robustesse du modèle :

- **Accuracy** : 0.870
- **Precision** : 0.815
- **Recall** : 0.917
- **F1-score** : 0.863
- **ROC AUC** : 0.911

Le **recall élevé** est particulièrement important ici, car il montre que le modèle détecte correctement une grande majorité des patients réellement à risque.

## Analyse du seuil de décision

Une analyse de plusieurs seuils de décision a été réalisée afin d’aligner la classification avec l’objectif métier.

Le seuil de **0,5** apparaît comme le meilleur compromis entre :

- capacité de détection ;
- fiabilité des prédictions ;
- équilibre global du modèle.

Dans ce contexte, abaisser fortement le seuil améliore le recall mais augmente nettement les faux positifs. À l’inverse, relever le seuil rend le modèle plus conservateur mais augmente le risque de manquer des cas réels.

## Interprétation métier

Ce projet montre qu’un modèle simple peut déjà fournir une aide utile à la décision.

La régression logistique permet de :

- repérer les variables les plus associées au risque ;
- mieux comprendre les profils patients à surveiller ;
- soutenir une logique de **triage** ou de **priorisation**.

Le modèle ne doit pas être vu comme un outil de diagnostic autonome, mais comme un **outil d’aide à la décision** capable de signaler les profils nécessitant une attention particulière.

## Limites du projet

Ce projet présente plusieurs limites :

- le jeu de données est de taille réduite ;
- les résultats doivent être interprétés avec prudence ;
- les associations observées ne doivent pas être lues comme des relations causales ;
- le modèle nécessite une validation sur des données plus larges avant tout usage réel.
