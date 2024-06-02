# Généralités

Le bateau est alimenté en électricité par deux panneaux solaires de 300 W.  

> [!TIP]  
> Voir si on ne peut pas trouver mieux car choisi le *30/07/2023*  

Deux faisceaux de câbles sont prévues, 1 pour les câbles de puissance et un autre pour les câbles d'informations. Pour éviter la déformation des signaux par les champs électromagnétiques des câbles de puissances, les deux faisceaux seront séparés de chaque côté des boites. (Cf rendu provisoire ci-dessous)  

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/FaisceauxElectrique.png?raw=true" alt="Rendu provisoire des faisceaux électrique" width=600/>  

Le faisceau de puissance est représenté en rouge. Les câbles de puissance représentent tous les câbles qui n'ont pour unique vocation d'alimenter les différents équipements.  
Le faisceau d'information est représenté en bleu. Les câbles d'information sont tous les câbles qui transmettent de l'information aux équipements, cela peut être des données ou des ordres. Par exemple, les données de la baie de capteurs envoyés au PC ou les directives données par le PC pour commander les vérins, les moteurs ou tout autre équipement.  

Pour éviter le bruit dans les signaux, surtout ceux qui nécessitent une grande précision, il est nécessaire de blinder certain des câbles (coût plus élevé).

Les faisceaux électriques sont des tubes en PVC avec des raccords en **T** pour dispatcher les bons câbles dans les bonnes boites. Ils seront placés le plus haut possible pour qu'en cas d'avarie, l'eau ne puissent pas rentrer dedans facilement.  

De plus, la baie de capteur est alimenté par le haut de chaque côté par un flexible étanche, un pour l'information et un pour la puissance comme toujours (Se référer à l'[arrangement](BaieDeCapteur#arrangement) de la baie de capteur pour plus de détail). D'où le choix de faire passer les faisceaux à l'extérieur.

Dans la boite n°3, il est prévu de mettre le contrôleur de charge ainsi que le boîtier à fusible. Les deux seront monter sur rails verticaux à l'intérieur des boites afin de pouvoir manipuler les équipements plus facilement.

# Cahiers des charges

## Cahier des charges - Autonomie énergétique

| Fonction | Critère | Niveau | Flexibilité |
| ----- | ----- | ----- | ----- |
| Autonomie en mode normal sans source de puissance apportée | Temps d'utilisation | 72 h | - 6 h |
| Autonomie en mode dégradé sans source de puissance apportée | Temps d'utilisation | 7 jours | - 1/2 jour |
| Avoir une batterie de secours pour envoyer des signaux de détresse* | Temps d'utilisation | 7 jours | / |
| Respect du budget | Prix | < 2500 € | 1000 €
| Fiabilité, robustesse et durabilité | Matériaux et équipement résistant dans le temps | / | / |
| Les batteries doivent pouvoir rentrer dans les boites | / | / | / |
| Les panneaux solaires doivent loger sur les bras des flotteurs | 125x110 cm | / | / |
| Les panneaux solaires doivent résister au milieu marin | Durabilité | Excellente | / |
| Être capable de charger les batteries en plus d'alimenté le système lors de condition normale | $\frac{Production}{Consommation}$ | > 1 | / |

*Consommation inférieure à 1 Wh avec déclenchement automatique en cas d'avarie majeure.



# Schéma électrique

> [!WARNING]
> Le schéma électrique est à compléter. Il ne représente pas toutes les connexions à ce jour !

## Esquisse du schéma électrique du Zéphyr

### Complet

Représente les connexions des différents éléments du Zéphyr  

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/electrical_diagram.png?raw=true" alt="Squelette du Zéphyr" width=400/>

### Puissance
Représente les connexions pour transmettre du courant aux éléments du Zéphyr  

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/power_diagram.png?raw=true" alt="Squelette du Zéphyr" width=400/>

### Information
Représente les connexions pour transmettre de l'information aux éléments du Zéphyr  

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/info_diagram.png?raw=true" alt="Squelette du Zéphyr" width=400/>

