# Architecture système du Zéphyr

Cette partie documente l'architecture de commande du voilier dans ses différents modes, elle est inspirée de l'architecture de l'[AutoNaut](https://autonaut.itk.ntnu.no/doku.php?id=start).

On a défini ici 3 niveaux de la même manière qu'en programmation, du plus proche au plus loin du Hardware :
- Hardware et contrôle global
- Navigation, mission et contrôle
- Capteur et sonde pour la science

## Hardware et contrôle global

C'est à ce niveau que la communication entre l'opérateur et le Zéphyr se fait, il fait aussi intervenir tous les équipements servant directement à faire avancer le bateau.  
* Iridium (Module de communication satellite)
* Communication LoRa (onde radio)
* Panneau photovoltaïque et batteries
* Moteurs et vérins


## Navigation, mission et contrôle

Dans ce niveau se trouve tous les algorithmes de décision du bateau, on y trouve aussi tous les capteurs de compréhension de l'environnement extérieur.  
* GPS
* Station météo
* Caméras
* Lidar
* Sonar
* Centrale inertielle
* Modem Milesight UR35
* AIS
* Iridium
* Communication LoRa


## Capteur et sonde scientifiques

Dans ce niveau se trouve tous les équipements que le Zéphyr embarquera à bord pour compléter ses missions scientifiques. Cette partie est donc à compléter une fois que l'utilisation du bateau a été définie.

> [!TIP]
> Ce niveau fait remarquer la possible nécessité d'un autre ordinateur de bord pour gérer les flux de données des différents capteurs.  
> Une baie de stockage d'information sera aussi à ajouter afin de garder les logs des capteurs

## Schéma

Schéma récapitulatif :



# Niveau 0



# Niveau 1

Nous choisirons dans le cas du Zéphyr un contrôleur de charge de type MPPT pour (Maximum Power Point Tracking), ce type de régulateur permet de maximiser l'énergie extraite des panneaux solaire même si les conditions varient. Il a un très bon rendement (meilleur que le régulateur PWM) et permet d'augmenter la durée de vie des batteries. [Wikipédia](https://en.wikipedia.org/wiki/Maximum_power_point_tracking).

Deux nombres sont marqués sur les contrôleurs de charges, le premier (150 dans notre cas) est la tension à vide du parc de panneaux photovoltaïque. Le deuxième nombre séparé par une barre (35 dans notre cas) est le courant maximal que le contrôleur est capable de transmettre aux batteries, il est très important que cette valeur soit en dessous de l'intensité maximale en charge des batteries.
Il est possible d'avoir une idée du dimensionnement du régulateur de charge en allant directement sur le site de [Victron Energy](https://www.victronenergy.fr/mppt-calculator)

Dans notre cas, nous avons choisi le Victron Energy 150 | 35 ([lien](https://www.myshop-solaire.com/regulateur-solaire-mppt-150-35-12-24-36-48v-victron-energy-_r_688_i_12.html))
La tension à vide de notre parc de panneaux ne dépasse pas les 43.52 V pour deux panneaux de 300W en parallèle ([lien](https://www.seimi-equipements-marine.com/fr/electricite-marine/panneaux-solaires/panneaux-solaires-rigides/panneau-solaire-spectra-/pdt_9498)). Le système est surdimensionné à 40% d'après les calculs du dimensionnement par Victron Energy.

Câblage du MPPT à la page 13 du [manuel de montage](https://www.victronenergy.com/upload/documents/Manual_SmartSolar_MPPT_150-35__150-45/29694-MPPT_solar_charger_manual-pdf-en.pdf) de Victron Energy

Convertisseur DC-DC 24V vers 12V ([lien](https://www.myshop-solaire.com/victron-energy-chargeur-orion-tr-smart-isole-dc-dc-24v-12v-20a-240w--_r_804_idr_804_i_2767.html)).

Stepper motor controler à déterminer pour pouvoir compléter le niveau 1.


# Niveau 2

## Liste des sorties d'information de l'ordinateur de bord

### Commandes
- Commande du moteur pas à pas du mat n°1
- Commande du moteur pas à pas du mât n°2
- Commande du vérin du volet de la voile n°1
- Commande du vérin du volet de la voile n°2
- Commande du vérin du gouvernail

### Information environnement
- Centrale météo
- GPS
- Centrale inertielle
- Caméras
- LIDAR
- SONAR
- Capteur de température de toutes les boites
- Capteur hygrométrique de toutes les boites

### Communication
- Iridium
- AIS
- LoRa
- Miesight UR 35

### Baie de capteur


## Navigation

### Algorithmes

#### Évitement d'obstacle