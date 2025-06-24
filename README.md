# Projet avec 
![image](https://github.com/user-attachments/assets/17e5beb1-9063-4894-b922-ae923b49e77f)

## Présentation du Groupe BPCE
Le Groupe BPCE est le 2ᵉ acteur bancaire en France, avec 100 000 employés au service de 36 millions de clients dans le monde. Il est actif en banque de détail, assurance, gestion d’actifs et banque d’affaires, à travers des marques comme Banque Populaire, Caisse d'Épargne, Palatine et Natixis.

# Contexte stratégique et marketing
Dans un marché centré sur la satisfaction client, la banque vise à mieux comprendre et anticiper les besoins pour fidéliser et rentabiliser sa clientèle. Elle souhaite utiliser un scoring automatisé pour optimiser l’octroi de la Carte Visa Premier.
Le scoring d’appétence attribue un score à chaque client selon sa probabilité d’intérêt pour une offre. Il permet d’améliorer l’efficacité des campagnes marketing car il ciblae les clients les plus succeptibles d'être intéressés par la carte. Ce projet de data mining prédictif vise à tester cette approche.

Une base de 1 063 clients de La Réunion, avec des données fiables issues du système d’information, a été collectée. La variable cible (détention de la carte) est accompagnée de 34 variables explicatives sélectionnées pour l’analyse.

# Données disponibles et préparation méthodologiques
Une base de 1 063 clients de La Réunion, avec des données fiables issues du système d’information, a été collectée. La variable cible (détention de la carte) est accompagnée de 34 variables explicatives sélectionnées pour l’analyse. Les données préparées seront traitées via le logiciel SAS dans le premier rapport et avec R dans le second rapport. 

- La principale contrainte dans un premier temps as été le souci d'interprétabilité. Sur ce, nous avons donc utilisé dans le rapport intermédiaire : Analyse en Composantes Multiples (ACM) + Clustering + Régression logistique
- Dans un deuxième temps, il faut garder cette interprétabilité mais aussi une performance très élevée en prédiction. Nous avons donc utilisé : Règle d'associations + Test sur le classifieur bayésien  ou SVM (efficace en petite taille de données). 

# Grandes découvertes sur le rapport intermédiaire
## ACM + méthodes de Clustering : Entre performance et interprétabilité
- ACM nettoie, simplifie, visualise → meilleure base.
- Clustering exploite cet espace → groupes plus stables, homogènes et lisibles.
- Résultats plus robustes et interprétables.

## ACM + méthodes de Clustering + Régression logistique : Entre performance, interprétabilité et prédiction
- On implémente une régression logistique dont la sortie finale renseigne le nombre de points par les modalités des variables
- Via chaque cluster formé par plusieurs modalités de quelques variables , on définit la somme de score des modalités de chaque cluster
- Dans notre cas, les clusters avec +60 scores sont classés appétentes
- Les scores entre 6 et 60 sont potentiellement appétentes
- Les scores moins de 6 sont moins pleausibles, pas très intéressants.

## Signification du mot prédiction
- Avec des nouveaux clients, le modèle est capable de dire s'il est appétent au produit ou non.
- Le modèle peut avoir raison comme par exemple : prédiction de l'appétence et le client est réellement appétent
- Il est possible de mieux expliquer le choix du modèle en comparant les caractéristiques de l'individu par rapport aux classes prédéfinies.

## Métriques d'évaluation 

|                      | Prédit : Négatif     | Prédit : Positif     |
|----------------------|----------------------|-----------------------|
| **Réel : Négatif**   | Vrai Négatif (TN) : 85 | Faux Positif (FP) : 15 |
| **Réel : Positif**   | Faux Négatif (FN) : 10 | Vrai Positif (TP) : 90 |

## Courbe de ROC
- Pour tracer une courbe de ROC, il y a plusieurs matrice de confusion correspondant à différents seuils :
| Seuil | TP | FP | TN | FN | TPR (Rappel) | FPR   |
|-------|----|----|----|----|--------------|-------|
| 0.9   | 40 |  5 | 90 | 60 | 0.40         | 0.052 |
| 0.7   | 65 | 10 | 85 | 35 | 0.65         | 0.105 |
| 0.5   | 80 | 20 | 75 | 20 | 0.80         | 0.210 |
| 0.3   | 90 | 35 | 60 | 10 | 0.90         | 0.368 |
| …     | …  | …  | …  | …  | …            | …     |

- On trace ensuite tous les points (FPR, TPR) sur un graphique et celà donne la courbe de ROC.
- Plus la courbe de ROC se rapproche de 1, plus le modèle détecte beaucoup de vraie positif sans faire beaucoup d'erreur sur les négatifs.
- Il peut comprendre la différence entre le Oui et le Non donc.
- On dit que le modèle est significativement performant s'il fait mieux que 0.5. 



# Grandes découvertes sur le rapport final
## Avant d'utiliser un modèle, il est nécessaire de bien comprendre les paramètres auquels il se repose. 
- Nous implémenté par exemple ici une règle d'association dont les trois paramètres sont visualisées dans le graphique ci-dessous
![image](https://github.com/user-attachments/assets/0abd44be-4791-41cd-bb57-f8118377898f)
- Chaque indicateur a été décrit et expliqué en page 7 et 8.


# Petite découverte 1 :  J'ai découvert comment on met en place d'une cohérente les statistiques exploratoires multidimensionnelles qualitatives se font en quelques sections très complémentaires :
##  Section 1 : Première caractérisation
### Etape 1 : Choisir les variables actifs et passifs mais non pas les axes optimaux 
- L'analyse multidimensionnelle consiste à représenter en quelques axes principaux qui synthétisent les informations des variables explicatives pour expliquer la variable à expliquer.
- La première étape cependant ne consiste pas à choisir le nombre d'axes optimaux comme d'habitude font les analystes de données.
- Il s'agit plutôt de choisir les variables actives dans ce sens qu'elles contribuent à construire les axes
- Dans notre cas, il s'agit des variables correspondant aux caractéristiques sociales de données bancaires.
  
## Etape 2 : L'analyse de la relation des modalités intra_variables ou/et entre les variables qualitatives : 
- Cette analyse passe par l'analyse des informations apportées avant tout par les deux premières axes principales.
- Visuellement, les modalités qui s'éloignet du centre sont significatives.
- Puisqu'elles ont un cosinus plus élevé et proche de 1.
- Les modalités qui sont proches selon un axe sont liées positivement.   
- Voici un exemple d'analyse de la première axe dans la page 03 :  On retrouve des clients plus créditeurs, qui affectent beaucoup de transactions à la banque opposés à des clients qui ont une moyenne de mouvement net créditeur faible, moins de transactions, sans emploi ou ouvrier

## Etape 3 : L'analyse de la typologie des individus selon les modalités de la variable à prédire (en particulier la propriété de la carte Visa Premier ou non)
- Il faut projetter maintenant les entités statistiques (unité d'étude comme le client ici) sur les modalités et caractériser la nature des individus 
- Exemple 1 : Cela indique que les plus grands utilisateurs de la carte Visa Premier sont majoritairement des hommes de catégorie socioprofessionnelle élevée, occupant des postes à responsabilité dans une entreprise. Ces profils à revenu élevé présentent également un solde bancaire en hausse.
- Exemple 2 : À l’inverse, les personnes aux caractéristiques opposées se retrouvent dans l’autre groupe.

## Section 2 : Deuxième caractérisation et certaines caractérisations

## Etape 4 : Choisir les axes 
- On ajoute toutes les variables maintenant
- Les valeurs propres des axes reflèttent les informations qu'elles contiennent
- Il faut donc supprimer les axes qui commencent à contenir moins des valeurs propres et donc d'informations

## Etape 5 : Bien définir les variables porteures 
- A chaque axe, il faut bien signaler les variables qui portent le plus chaque axe selon le principe ci-dessus
- Exemple de l'axe 1 et 2 : Moyenne de mouvement Créditeur, nombre de transactions et catégorie professionnelle
- Exemple de l'axe 1 et 3 : précision sur la relation entrecatégorie professionnelle, moyenne des mouvements crédit et e compte à vue
- Exemple de l'axe 3 et 5 : avoir un épargne et un nombre de produits épargnés

## Etape 6 : Ajouter les informations apportées par les autres variables 
- D'habitude, il y a plus de 02 axes qui sont significatives. 
- On ajoute les informations cohérentes avec les deux axes des autres axes et éventuellement les individus les plus représentatifs
- Exemple : les clients jeunes n'ont pas d'emplois

# Petite découverte 2 :  La formule très simple mais fondatrice du clustering 
## La formule de R²
Il s'agit de : 
$$
R^2 \;=\;
\frac{\displaystyle \operatorname{Inertie}_{\text{inter}}}
     {\displaystyle \operatorname{Inertie}_{\text{totale}}}
$$

## Signification 
- Il faut maximiser d'une part l'inertie inter-classe par rapport à l'inertie totale pour avoir des classes différentes
- R² varit de 0 à 1 donc. Plus on se rapproche de 1, K-means est de plus en plus parfait.

# Amélioration du projet : 
- Resampling des données d'échantillonage pour éviter le biais liés au genre. En effet, nous avons trouvé (page 4) que les personnes qui utilisent le plus la carte Visa Premier sont les personnens de sexe Homme à revenu élevé, occupant une poste hiérarchique élevé au sein d'une entreprise. Le modèle que nous avons eu ici en final detient donc ce biais qui prédit que les Hommes sont plus appétents aux cartes de Visa Premier que les Femmes.
- Confusion de langage : K-means n'appartient pas dans la classification, c'est plutôt un clustering et donc non-supervisé. 
