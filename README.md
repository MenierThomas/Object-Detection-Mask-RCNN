# Détection de Sneakers avec Mask RCNN 

![test.jpg](assets/test.jpg)

## Description du Projet
Ce projet vise à détecter des sneakers dans des images en utilisant le modèle Mask-RCNN. Le modèle est entraîné pour prédire la présence de sneakers, en générant des masques de détection pour chaque instance détectée.

L'évaluation des performances du modèle est réalisée à l'aide d'une matrice de confusion et de graphiques représentant les pertes d'entraînement et de validation.

## Annotations 

Nous avons annotés un total de 390 images avec l'outils VIA 2.0.12, 300 images pour le training (250 images contenant des sneakers et 50 n'en contenant pas), 60 images pour la validation (50 vraies, 10 fausses) et 30 pour les tests (25 vraies, 5 fausses). 

![annotation.jpg](assets/annotation.jpg)

## Hyperparamètres

Le modèle a été entraîné avec le jeu d'hyperparamètres suivant :

| Hyperparamètre          | Valeurs utilisées                         |
|-------------------------|-------------------------------------------|
| **Taux d'apprentissage (lr)**  | 0.001                              |
| **Époques**              | 250                                      |
| **Taux de Dropout**        | 0.9                                   |
| **Initialisation des Poids** | mask_rcnn_coco.h5                     |

## Graphe des Pertes d'Entraînement et de Validation

Le graphique ci-dessous représente la perte (loss) sur l’ensemble d’entraînement et l’ensemble de validation au cours des différentes époques d'entraînement. Ce graphique permet d’évaluer si le modèle présente des signes de surapprentissage (overfitting) ou de sous-apprentissage (underfitting).

![Training and Validation Loss](assets/loss_graph.png)

Ici, on observe que la perte sur l'ensemble de validation est plus élevée que sur l'ensemble d'entraînement, indiquant que le modèle est en surapprentissage.

## Matrice de Confusion

La matrice de confusion suivante illustre la performance du modèle sur l’ensemble de test. Elle permet d’évaluer la qualité de la classification en comparant les prédictions du modèle avec les vraies étiquettes des données.

![Matrice de Confusion](assets/confusion_matrix.png)

Résumé de la matrice de confusion :
- Faux Positifs (FP) : 18
- Vrais Négatifs (TN) : 0
- Faux Négatifs (FN) : 8
- Vrais Positifs (TP) : 34
- Précision : 56,67%

## Résultats et Analyse

L’analyse des résultats montre que le modèle atteint une précision globale de 56,67% et présente également des signes de surapprentissage. Voici quelques observations clés :

- **Surapprentissage** : En observant les courbes de perte, le modèle montre des signes de surapprentissage. Différentes méthodes pourraient aider à corriger cela :
    - **Augmentation des Données** : Générer plus de variations dans le jeu d’entraînement (ex. rotations, redimensionnements) pourrait aider le modèle à mieux généraliser.
    - **Arrêt Prématuré** : En appliquant un arrêt prématuré, l'entraînement pourrait être interrompu lorsque la perte de validation commence à augmenter, pour prévenir le surapprentissage.
    - **Régularisation** : L’ajout d’une régularisation L1 ou L2, ou l’augmentation du dropout, pourrait réduire le surapprentissage en limitant la complexité du modèle.

- **Effet des Hyperparamètres** : 
    - **Taux d'Apprentissage** : Le taux d'apprentissage de 0.001 a permis une convergence rapide tout en maintenant la stabilité de l’entraînement.

--- 

