\# Compte rendu TP PetitPanier - TON NOM



Systèmes utilisés : Windows, Docker Desktop



### **## Palier 1**



1.1 :Le Client est la commande docker que je tape, elle envoie des ordres.

Le Server est le moteur Docker qui tourne en arrière-plan et qui construit

les images et lance les conteneurs. Si le bloc Server est absent, le client

ne peut pas joindre le moteur : Docker Desktop n'est pas démarré.

!\[preuve 1.1](preuves/preuve-1-1.png)



1.2 :Dans -p 8080:80, 8080 est le port de ma machine (celui que j'utilise

dans le navigateur) et 80 est le port du conteneur (celui sur lequel nginx

écoute). Docker redirige le port 8080 de ma machine vers le port 80 du conteneur.

!\[preuve 1.2 terminal](preuves/preuve-1-2-terminal.png)

!\[preuve 1.2 navigateur](preuves/preuve-1-2-navigateur.png)



1.3 :!\[preuve 1.3 logs](preuves/preuve-1-3-logs.png)

!\[preuve 1.3 image](preuves/preuve-1-3-image.png)



Une image est un modèle en lecture seule, stocké sur mon PC, qui contient

tout ce qu'il faut pour lancer un programme (ici nginx). Un conteneur est une

instance de cette image en cours d'exécution : il est créé à partir de l'image,

il a un nom, des logs et on peut entrer dedans. Après docker rm, le conteneur

essai a disparu de docker ps -a, mais l'image nginx:alpine est toujours là

dans docker image ls. On peut donc créer autant de conteneurs qu'on veut à

partir d'une même image, et supprimer un conteneur ne supprime pas l'image.





### **## Palier 2**

2.1 :!\[preuve 2.1](preuves/preuve-2-1.png)



2.2 : Non, EXPOSE 8080 ne suffit pas. Cette instruction sert seulement à

documenter le port sur lequel l'application écoute dans le conteneur, elle

ne le rend pas accessible depuis ma machine. Pour ouvrir la page dans le

navigateur, il faut publier le port avec -p au lancement du conteneur

(par exemple -p 8080:8080), ce qui relie un port de ma machine au port du conteneur.



2.3 :!\[preuve 2.3 image](preuves/preuve-2-3-image.png)

&#x20;   : !\[preuve 2.3 navigateur](preuves/preuve-2-3-navigateur.png)

&#x20;   : Le . à la fin de docker build indique le contexte de build : c'est le

dossier courant, que Docker utilise pour trouver le Dockerfile et les fichiers

à copier dans l'image (comme index.html). Ici on utilise -p 8080:8080 parce que

l'image nginx-unprivileged écoute sur le port 8080 dans le conteneur, alors que

l'image nginx du palier 1 écoutait sur le port 80. Le port à droite de -p doit

toujours être celui sur lequel l'application écoute dans le conteneur.



2.4 : !\[preuve 2.4 avant](preuves/preuve-2-4-avant.png)

&#x20;   : !\[preuve 2.4 images](preuves/preuve-2-4-images.png)

&#x20;   : !\[preuve 2.4 apres](preuves/preuve-2-4-apres.png)



&#x20;    :La page affichait encore la 1.0 parce que le conteneur qui tournait avait

été créé à partir de l'image 1.0. Construire une nouvelle image 2.0 ne modifie

pas un conteneur déjà lancé 

j'ai utilisé docker rm -f petitpanier

pour supprimer l'ancien conteneur, puis docker run --name petitpanier -d -p 8080:8080 petitpanier:2.0

pour en lancer un nouveau avec l'image 2.0.



\## Palier 3

3.2 :

3.3 :



\## Palier 4

4.1 :

4.2 :

4.3 :



\## Palier 5

5.1 :

5.2 :

5.3 :



\## Palier 6 - tableau de diagnostic

| Panne | Symptôme | Hypothèse | Commande de preuve et résultat | Correction |

|---|---|---|---|---|

| promo-1 | | | | |

| promo-2 | | | | |

| promo-3 | | | | |



6.2 (--previous) :

6.3 (pourquoi Running mais inaccessible) :



\## Palier 7

| Étape | Commande | Si échec |

|---|---|---|

| build | | |

| test | | |

| publish | | |

| deploy | | |



7.1 :

Workflow n8n :



\## Défis réalisés

