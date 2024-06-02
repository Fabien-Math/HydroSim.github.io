Cette page est dédiée à la coque !
# Généralités

Pour sa construction, la coque se décompose en 4 parties distinctes : 
* Le **squelette** en contre plaqué marine 5 mm
* L'**armature** en chevron
* La **forme** de la coque en polystyrène
* Le **nez** du Zéphyr démontable

Les 3 premières parties s'assemblent comme un puzzle pour le squelette, avec des vis pour l'armature et avec de la colle pour la forme. La dernière vient se fixer sur l'armature à l'avant du bateau.

La coque est composée de 5 parties vides nommées *boites* numérotées de **1** à **5**. Chaque boite possède une fonction.  

| Boite | N° Section | Description |
|-----|-----|-----|
| 1 | 3 | Matériel informatique et communication |
| 2 | 4 | Voile N°1 et batteries principales |
| 3 | 5 | Puits de dérive, contrôleur de charge et gestionnaire intelligent de la batterie |
| 4 | 6 | Voile N°2 et possiblement batteries (à déterminer) |
| 5 | 8 | Gouvernail et possiblement batterie (à déterminer) |


La boite N°1 sera complètement étanche et séparée des autres boites, une boite d'acquisition devra être faite sur mesure pour acheminer toutes les connectiques et les câbles d'alimentation aux différents éléments de cette boite.

Les boites suivantes, à savoir les boites N°2 à N°5 seront étanches les unes des autres dans le bas. Par contre, elles seront toutes reliées par les câbles d'alimentation électrique d'alimentation et d'information. (Pour plus d'information voir [Page Électricité](Electricite))

### Électricité
Pour ce qui est de l'électricité, il faudra faire sortir des câbles à l'aide d'une interface de connexion avec du 5, 12, et 24V pour pouvoir alimenter les équipements extérieurs au boites.

# Dimensions

## Coque
4680 mm long
581 mm high
692 mm wide

## Flotteur
2325 mm long
300 mm high
480 mm high (avec brides)
300 mm wide

## All at least this dimensions
4.7 m long
3.8 m high (overall)
3.3 m wide


# Squelette

Largeur des encoches des couples (Partie remplie sur les couples)
- couple 2 : 102.5 mm
- couple 3 : 145 mm
- couple 4 : 155 mm
- couple 5 : 160 mm
- couple 6 : 160 mm
- couple 7 : 150 mm
- couple 8 : 140 mm

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/Squelette.png?raw=true" alt="Squelette du Zéphyr" width=400/>

# Armature

L'armature est composée de deux types de chevrons, les plus gros en haut sont des chevrons de 50x75 mm traités en classe 2. Ceux du bas sont des chevrons de 38x63 ou 38x60 les côtes n'étant pas précises.  
C'est 4 chevrons traversent tout le bateau de l'avant à l'arrière. Sur ces chevrons sont fixés des **hauteurs**, les renforts verticaux et des **traverses**, les renforts horizontaux. À l'avant on retrouve un système de chevron afin de fixer le nez du Zéphyr qui est démontable.

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/StructureChevronCoque.png?raw=true" alt="Armature du Zéphyr" width=400/>



# Description plus précise de l'organisation des boites

## Boite N°1

Dans cette boite : tous les équipements peuvent être retrouvés [ici](Equipement#liste-des-équipements-présents-dans-le-zéphyr)
- LattePanda Alpha
  - Ordinateur de bord du Zéphyr
- Jetson Nano
  - Carte graphique du Zéphyr
- MileSight UR35
  - Modem WiFi et 4G avec GPS intégré
- AIS Modem
  - Permet de voir l'activité des bateaux aux alentours s'ils en sont équipés (Les gros bateaux sont obligés de diffuser sur l'AIS (Cf [source](https://www.voileetmoteur.com/voiliers/equipement/lais-en-10-questions/112158)))
- Accéléromètre
- Boussole magnétique
- 

### Plateforme suspendue
Une station suspendue sur amortisseur afin de remplir de rôle de plateforme anti-choc devra être conçu pour accrocher les composants électroniques du bateau dans cette boite.

> [!NOTE]
> *Faire une plateforme complètement suspendue est inutile. Il n'est pas nécessaire d'amortir les mouvements de rotation, cela rajouterais beaucoup de complexité au système alors que les PC ne craignent pas de fonctionner penchés s'ils sont biens ventilés.*  
> *La plateforme aura donc pour cahier des charges d'annuler les chocs liés à la retombée du bateau sur l'eau. Il reste donc à dimensionner les amortisseurs en fonction des chocs auxquels le Zéphyr pourrait être soumis.*

## Boite N°2

- Système de maintien de la voile N°1
- Réducteur du mât (Cf [Page voile](Voile#système-de-commande))
- Moteur du mât (Cf [Page équipement](Equipement#liste-des-équipements-présents-dans-le-zéphyr))
- Batterie principale (Cf [Page équipement](Equipement#liste-des-équipements-présents-dans-le-zéphyr))
- Passage des câbles d'alimentation (Cf [Page électricité](Electricite))
- Passage des câbles d'information (Cf [Page électricité](Electricite))
- Capteur de température
- Capteur hygrométrique
- 

## Boite N°3

- Puits de dérive (Cf [Page coque](Coque#Dérive))
- Système de fixation de la dérive (Cf [Page coque](Coque#Dérive))
- Contrôleur de charges des batteries (Cf [Page équipement](Equipement#liste-des-équipements-présents-dans-le-zéphyr))
- Passage des câbles d'information (Cf [Page électricité](Electricite))
- Capteur de température
- Capteur hygrométrique

Dans cette boite, les équipements sont sur des glissières leurs permettant d'être relevé grâce à une poignée. Fixé sur les deux lambourdes sur les côtés de la boite. Les câbles des équipements doivent être assez grand pour que relevé le plan ne tire pas sur les câbles. [Type de glissières pensé](https://www.leroymerlin.fr/produits/quincaillerie/quincaillerie-du-meuble/compas-verin-coulisseau-coulisse/lot-de-2-coulisses-pour-tiroir-a-billes-hettich-45-kg-l-25-cm-70206941.html)
> [!WARNING]
> La taille entre le puits de dérive et le bord de la boite est exigu, il est donc nécessaire que le système soit le plus compact possible.

> [!WARNING]
> Regarder comment fixer les câbles sur le contrôleur de charge, ils peuvent être dirigés vers le puits de dérive. Regarder pour acheter des coudes pour des connexions plus fiables

## Boite N°4

- Système de maintien de la voile N°2
- Réducteur du mât (Cf [Page voile](Voile#système-de-commande))
- Moteur du mât (Cf [Page équipement](Equipement#liste-des-équipements-présents-dans-le-zéphyr))
- Batterie principale (Cf [Page équipement](Equipement#liste-des-équipements-présents-dans-le-zéphyr))
- Passage des câbles d'alimentation (Cf [Page électricité](Electricite))
- Passage des câbles d'information (Cf [Page électricité](Electricite))
- Capteur de température
- Capteur hygrométrique
- 

## Boite N°5

Partie à réaliser après le projet de 1A



# Dérive

La dérive se logera dans un puits de dérive et sera statique. Elle sera fixée par 3 vis (*M16 pour le moment*) pour que chaque vis soit supporte un effort (principe d'un tabouret à 3 pieds) et que les moments induits par l'eau sur la dérive soit annuler efficacement. Les trois vis sont situées au-dessus de la ligne de flottaison pour un poids total de la coque de **540 kg**.  

Les dimensions de la dérive sont données par la mise en plan suivante (Conception 3D sur Fusion360 : "*Derive/DeriveZephyr*") :

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/PlanDerive1.png?raw=true" width=400 alt="Plan 1/2 de la dérive" title="Plan dérive 1/2">

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/PlanDerive2.png?raw=true" width=400 alt="Plan 2/2 de la dérive" title="Plan dérive 2/2">


## Puits de dérive

Pour calculer les dimensions du puits de dérive, on a pris 2 mm de marge de chaque côté pour l'étanchéité avec le raccord de stratification et 1 cm de plus pour avoir une marge pour positionner la dérive plus facilement. On arrive donc à une longueur intérieure de 410 mm.

Pour faire une structure plus solide, tout le puits de dérive sera fait en contre plaqué marine okoumé de 15 mm d'épaisseur. Pour le construire, on colle et vis les deux parties *left side bottom* à la *left side* (idem pour les pièces "*right ...*") puis on assemble les parties en collant et vissant *front* et *back* sur les *left side* et *right side* assemblées (Cf schémas ci-dessous). La partie *top* se vis avec un joint en néoprène. **Les vis restent à placer sur la conception.**

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/VueEclateeDerive.png?raw=true" width=400 alt="Vue 3D du puits de dérive" title="Vue 3D du puits de dérive">

<img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/PlanPuitsDeDevrive.png?raw=true" width=400 alt="Plan du puits de dérive" title="Plan du puits de dérive">


## Montage

Pour monter la dérive, la solution envisagée (24/02/2024) est de lever le bateau à l'aide de poulies directement sur la remorque, on y glisse ensuite la dérive dans le puits et on visse cette dernière en s'assurant que les joints sont biens mis pour étanchéifier ses points de fixation. Cela nécessitera au moins 2 personnes.  
On peut facilite le montage en ajoutant des aimants dans le puits de dérive et dans la dérive afin de la guider.


> [!NOTE]
> *Les solutions écartées sont de mettre la dérive une fois le bateau dans l'eau à l'aide d'un plongeur. Cette solution est dangereuse pour le plongeur car le bateau ne pèsera pas moins de 600 kg une fois tout monté avec ses lests et nous n'en auront aucun contrôle au moment de la mettre. De plus, il faudrait, pour facilité le montage de la dérive un système de clips (déjà pensé, cf image ci-dessous ou conception 3D sur Fusion360 : Derive/Derive auto-lock) mais bien plus difficile à mettre en œuvre.*  
> <img src="https://github.com/HydroSharks/ZephyrWiki/blob/main/PuitsDeriveAutoLock.png?raw=true" width=400 alt="Plan du puits de dérive auto-lock" title="Plan du puits de dérive auto-lock">  
> *Les parties rouges sont des goupilles (optionnelles), la dérive tient grâce à des encoches et une barre de retenu. Pour facilité le montage, des aimants ont été incrustés dans le puits de dérive et dans la dérive.*