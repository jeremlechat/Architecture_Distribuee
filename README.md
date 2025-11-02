# Rendu personnel :

## TD1

### Question 2 

Le fichier package.json contient les informations générales à propos du template typescript fourni comme son nom, son auteur, sa licence mais surtout l'ensemble des dépendances nécessaires au projet ainsi que leur veresion minimale.
Le fichier package-lock.json contient l'ensemble des dépendances et sous dépendances du projets ainsi que les versions exactes associées au projet.

### Question 3

L'installation de la bibliothèque systeminformation ajoute la ligne suivante dans le fichier package.json :
```json
"dependencies": {
    "systeminformation": "^5.27.11"
```

`dependencies` et `devDependencies` contiennent les dépendances du projet mais `devDependencies` contient celles voulues par le développeur original tandis que `dependencies` contient celles rajoutées par l'utilisateur.

### Question 4

La principale difficulté fut le codage en TS, un langage que je ne connais pas.

### Question 5

On utilise ce formalisme afin de garder un code propre et facilement maintenable.

### Question 6

Le but d'écrire un tel jeu de test est de vérifier que la structure de la sortie est respectée ou que les données renvoyées sont correctes.


## TD2


### Question 4 

- Le flag -p sert à mapper un des ports de ma machine physique sur un port du container.

- Le flag -m sert à limiter la quantité de mémoire RAM allouée au conteneur en tuant le processus si il est trop gourmand.

- Le flag --cpus sert à limiter la puissance des cpus mis à disposition du conteneur.

Les seules options qui peuvent impacter l'application sont -m et --cpus en la tuant ou en la ralentissant si le nombre de cpus est sous-dimensionné.

### Question 5 

L'outil dive nous permet d'analyser en profondeur l'image crée. Je ne comprends pas comment on pourrait réduire l'image car docker est censé offrir l'image la plus légère possible. Il faudrait alors offrir une application source plus simple.

### Question 6 

L'image construite de manière multi-stage pèse 173MB contre 391MB pour la première image. En ne conservant que les fichiers nécessaires au run de l'application on gagne beaucoup de place. Cela veut dire qu'on peut déployer des applications en multistage qui seraient trop lourde en monostage.

### Question 8

J'utiliserai la commande `sh
docker pull
`

## TD3 

### Intégration Continue

#### Question 2 

Pour créer les tests j'ai [utilisé ChatGPT](https://chatgpt.com) ainsi que la [documentation Github](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax) 

#### Question 3 

Pour lance les tests, je vais dans l'onglet Action puis je clique sur le nom du test et enfin je clique sur le bouton pour lancer les tests dans le sous onglet latéral Jobs

#### Question 4

La question était *Écrivez un jeu de tests pour votre application avec Jest, et vérifiez son exécution. Pourquoi écrit-on un tel jeu de tests ?*

L'objectif du jeu de test est de les vérifier à commit pour garantir que la nouvelle version est toujours fonctionnel et ne détériore pas certaines caractéristiques du projet.

### Livraison Continue

On utilise les secrets Github pour éviter les problèmes de sécurité et de divulgation de mots de passe.

J'ai eu de nombreux pronblèmes concernant la mise en place du test de publication de l'image Docker, le principal concerne les permissions accordées aux workflows. Vu que le workflow de publication est lancé par la réussite de l'intégration continue il a fallu accorder les permission en écriture aux deux. De plus l'emploi d'un secret simple ne foncitonnant pas j'ai utilisé un token d'accès personnel. Je pensais que le nom de l'image à publier était sensible à la casse mais finalement non, il n'a pas besoin d'être identique au nom du dépôt. Finalement l'erreur venait d'un problème d'accès du Token Docker et non pas de GitHub Container Registry. 
