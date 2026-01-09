# Power BI : Gérer des environnements Python Conda


Python est un outil essentiel pour la gestion des données grâce à ses bibliothèques puissantes et sa syntaxe simple. L'intégration de Python dans Power BI offre des possibilités étendues d'analyse et de visualisation des données. Cependant, la gestion des dépendances et des environnements Python peut devenir complexe. Conda est un système de gestion de paquets et d'environnements open-source qui apporte une solution robuste à ces défis.

Ce répertoire GitHub contient l'ensemble des éléments utilisés dans cet article. Et une vidéo tutorial [Youtube](https://youtu.be/P_7lc7xEyNk) reprend également les éléments présentés dans cet article.

## Prérequis

- Power BI desktop installé

- Une distribution Anaconda ou Miniconda installée sur votre machine

## Raison d'utiliser Conda dans Power BI

- **Isolation des dépendances** : Cela permet de définir un environnement avec des versions de Python et des librairies spécifiques pour chaque projet.

- **Reproductibilité** : Cela permet de partager un fichier environment.yml pour définir et gérer des environnements reproductibles sur différentes machines ou par différents utilisateurs.

- **Gestion des conflits** : Cela permet de résoudre des problèmes de compatibilité entre librairies Python sans affecter les autres projets d'un utilisateur.

- **Versionning** : Cela permet de facilement gérer différentes versions de Python et ses librairies pour chaque projet indépendamment.

## Configuration de base d'un environnement Conda
Commencer par ouvrir une invite de commande et suivre les étapes suivantes pour configurer un environnement virtuel Conda :

### Créer un environnement virtuel Conda
Nous allons commencer par créer un environnement virtuel nommé *power_bi* en précisant la version de Python que nous souhaitons utiliser (*3.11*):

```bash
conda create --name power_bi python=3.11
```

### Activer l'environnement
Cette commande ca permettre d'activer l'environnement *power_bi* et de pouvoir y réaliser des installations : 

```bash
conda activate power_bi
```

### Installer des librairies Python
Il faut à minima installer les librairies pandas et matplotlib lorsque l'on souhaite utiliser Python depuis Power BI Desktop. Pour cela, nous recommandons d'utiliser la commande conda install car elle offre une gestion des dépendances plus robuste.

```bash
conda install pandas matplotlib
```


## Configuration dans Power BI
Commencer par ouvrir Power Bi Desktop puis suivre les étapes suivantes pas à pas.

### Activer les scripts Python

- Ouvrir Power Bi Desktop et suivre les étapes suivantes : 

    1. Cliquer sur **Options et paramètres**
    2. Cliquer sur **Options**

![Ouverture du menu Option dans Power BI](images/PBI%20-%20Configuration%2000.png)


- Après l'ouverture de la fenêtre **Options**, réaliser les étapes suivantes : 

1. Depuis le volet **Global**, sélectionner l'option **Création de scripts Python**

2. Dans le champ **Définir un répertoire de base Python**, inscrire le chemin vers l'installation de l'environnement Conda que l'on souhaite utiliser depuis Power BI

3. Cliquer sur le bouton **OK** pour fermer la fenêtre

![](images/PBI%20-%20Configuration%2001.png)


Pour trouver les chemins d'installation des environnements Conda sur votre machine : Ouvrir une invite de commande Windows et entrer la commande suivante :

```bash
conda env list
```

### Vérification de l'installation

- **Ouvrir l'éditeur de script Python**

Depuis l'éditeur Power BI, suivre les étapes suivantes : 

1. Cliquer sur le menu **Obtenir les données**

2. Choisir l'option **Plus**. Cela va ouvrir la fenêtre **Obtenir les données**.

![](images/PBI%20-%20Script%20Python%200.png)


Depuis la fenêtre **Obtenir les données**, suivre les étapes suivantes : 

1. Depuis le volet de gauche, choisir **Autre**

2. Parmi les différentes options proposées, choisir **Script Python** 

3. Cliquer sur **Se connecter**. Cela va ouvrir la fenêtre **Script Python** dans laquelle vous pourrez écrire votre code Python.

![](images/PBI%20-%20Script%20Python%201.png)


- **Tester un script simple**

Voici un simple script Python permettant de créer un Dataframe Pandas:

```python
import pandas as pd
df = pd.DataFrame({'Test': [1, 2, 3]})
```


Depuis la fenêtre **Script Python** :

1. Copier-coller le code Python ci-dessous dans le champ **Script**

2. Cliquer sur le bouton **OK** pour fermer la fenêtre et lancer l'exécution du code

![](images/PBI%20-%20Script%20Python%202.png)

Si le code s'exécute sans erreur, la fenêtre **Navigateur** s'ouvre pour proposer soit de **Charger** les données qui ont été crées ou bien de **Transformer les données** comme illustrer dans l'image suivante : 

![](images/PBI%20-%20Navigateur%202.png)

## Gestion avancée

L'avantage d'utiliser le gestionnaire de paquets Conda est de pouvoir partager cet environnement. Après avoir activer son environnement, il suffit de taper la commande suivante:

```bash
conda env export > environment.yml
```

Le fichier *environment.yml* va pouvoir être partagé pour permettre de reproduire l'environnement utilisé dans un projet sur d'autre machine.

## Recommandations

1. Développer et tester ses scripts Python dans l'environnement Conda

2. Exporter la liste des dépendances

3. Configurer Power BI pour utiliser cet environnement

4. Versionner le fichier *environment.yml* avec son projet Power BI

## Conclusion

Cette article a montré comment gérer et utiliser des environnements Conda pour les scripts Python dans Power BI.

L'utilisation de *Conda* pour gérer les environnements Python offre structure et reproductibilité à un projet d'analyse de données. En permettant d'isoler les dépendances, on garantie la portabilité des solutions et permet d'éviter les problèmes de compatibilité. *Conda* devient un outil indispensable dans la boîte à outils Power BI pour les équipes travaillant sur plusieurs projets à la fois.


## [Vidéo Youtube](https://youtu.be/P_7lc7xEyNk)

- [Introduction](https://youtu.be/P_7lc7xEyNk&t=00m00s)
- [Créer un environnement Conda](https://youtu.be/P_7lc7xEyNk&t=00m08s)
- [Activer l'environnement Conda](https://youtu.be/P_7lc7xEyNk&t=00m35s)
- [Installer des packages Python](https://youtu.be/P_7lc7xEyNk&t=00m50s)
- [Activer les scripts Python dans Power BI](https://youtu.be/P_7lc7xEyNk&t=01m21s)
- [Vérification de l'installation dans Power BI](https://youtu.be/P_7lc7xEyNk&t=01m52s)