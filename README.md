# Grande découverte 1 :  J'ai découvert comment on met en place d'une cohérente les statistiques exploratoires multidimensionnelles qualitatives se font en quelques sections très complémentaires :
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

# Grande découverte 2 :  La formule très simple mais fondatrice du clustering 
Il s'fait de : 
R^2 = \frac{\text{Inertie inter-classe}}{\text{Inertie totale}}


# Amélioration du projet : 
- Resampling des données d'échantillonage pour éviter le biais liés au genre. En effet, nous avons trouvé (page 4) que les personnes qui utilisent le plus la carte Visa Premier sont les personnens de sexe Homme à revenu élevé, occupant une poste hiérarchique élevé au sein d'une entreprise. Le modèle que nous avons eu ici en final detient donc ce biais qui prédit que les Hommes sont plus appétents aux cartes de Visa Premier que les Femmes.
- Confusion de langage : K-means n'appartient pas dans la classification, c'est plutôt un clustering et donc non-supervisé. 
