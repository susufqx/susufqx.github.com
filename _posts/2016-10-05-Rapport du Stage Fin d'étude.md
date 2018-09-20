---
layout: post
title: "Rapport du Stage Fin d'étude"
date: 2016-10-05 00:14
categories: blog
header-img: /images/paris.jpg
tags:
- Meteor
- JavaScript
- GoogleMaps API
- Semantic-UI
- Node.JS
- Mailjet
- Sitemap
- MongoDB
- underscore.JS
- jQuery
- Grid Files
- JSON
---

### Développement du Web de front-end et back-end en Meteor.JS

#### Catalogue

* [I. LA SOCIÉTÉ MYLITTLE WORKER (MLW)](#1)
* [II. METEOR.JS, SEMANTIC-UI ET AUTRE CHOSES](#2)
* [1.METEOR.JS](#2.1)
* [2.SEMANTIC-UI](#2.2)
* [3.AUTRE CHOSES](#2.3)
* [III. LES MISSIONS](#3)
* [1.CREER LES PAGES ET REALISER LES CONTROLER](#3.1)
* [2.PACKAGE DE DBURLES : GOOGLE-MAPS](#3.2)
* [3.GOOGLE MAPS API DE PLACES](#3.3)
* [4.FICHIER DEPOSER PACKAGE DE VSIVSI/METEOR-FILE-COLLECTION](#3.4)
* [5.SITEMAP](#3.5)
* [IV. LES CONNAISSANCES APPRIS EN STAGE](#4)
* [V. CONCLUSION](#5)

<h4 id="1">I. LA SOCIÉTÉ MYLITTLE WORKER (MLW)</h4>

C’est une startup créé cette année. Je ne sais pas très beaucoup de la société.

En stage, on fait le web qui est la principale de la société. C’est un web pour la maison et on peut trouver les techniques supporter par le web. Si on a besoin de faire quelque chose à la maison on peut trouver les travailler sur MLW. Et le web est en développement à ce moment donc on ne peut pas utiliser le web et seulement test le web. C’est le début de la startup.

<h4 id="2">II. METEOR.JS, SEMANTIC-UI ET AUTRE CHOSES</h4>

En stage, ma mission est le développement du web. C’est un développement full-stack donc j’ai besoin de faire le front-end et back-end. Dans cette partie, je veux présenter les frameworks ou les bibliothèques j’ai utilisé en stage. Il y a deux frameworks essentiels que on doit étudier beaucoup, ils Meteor.JS et Semantic-UI.

<h5 id="2.1">1.METEOR.JS</h5>

En fait, Meteor est un framework open-source de développement web en JavaScript basé sur Node.js. Le projet vise à créer un framework de « nouvelle génération » induisant un changement de paradigme notamment sur la manière de considérer les architectures client-serveur. On veut donner un diagramme pour expliquer le travail de Meteor :

![avatar](/images/blogs/2016-10-05-01.jpeg)

L’application du web a deux partis : front-end et back-end ou on peut utiliser client et serveur. Client est pour les utilisateurs et serveur est l’ordinateur qui donner le client les données et contrôler les logiques de l’application.

Meteor est full-stack framework donc il a front-end et back-end. On peut écrire les deux partis en la même langage-JavsScript. Seulement JavaScript peut fonctionner dans le front-end et aussi back-end. On peut partager le code entre front-end et back-end.  C’est très bien pour les développeurs du web parce que ils n’ont pas besoin d’apprendre JavaScript pour le front-end et autre langage pour le back-end comme JavaEE, ASP.NET, PHP etc.   

On n’a pas besoin de connaître comment Meteor fonctionner entre les deux partis. Back-end, on peut utiliser le Meteor.JS et Node.JS. En fait, Meteor.JS est seulement l’autre type de Node.  

Node est le langage de back-end mais le front-end on peut utiliser quoi ? Bien sûr, on a trois options sur le document officiel. Les trois sont Blaze.JS, Angular.JS et React.JS. Je pense que Angular.JS et React.JS sont très connu pour les ingénieurs du Web. Si on choisit Angular.JS ou React.JS, c’est facile de modifier le back-end par Meteor ou c’est facile d’utiliser autres langages du back-end. Mais dans notre projet, on a choisi Blaze qui est plus simple et seulement peut être utilisé dans Meteor. Blaze n’est pas complexe mais il est très puissant qui peut on aide d’écrire le front-end très bien. Il a le mécanisme de Template qui peut ajouter les datas dans le fichier HTML. Il a beaucoup de méthodes pour nous de faire les datas afficher dans le client mieux.

C’est facile pour nous de faire le développement du web. Après installer Meteor sur nos ordinateurs, on peut créer le nouveau projet sur le Terminal par :
```
$ meteor create MyProject
```
Ça a créé le projet qui s’appelle MyProject, le carton MyProject contient les fichiers de Meteor. Il y a beaucoup de types de cartons dans le carton MyProject. Client et Server sont obligatoire. Tous les code dans le Client peuvent seulement marcher dans le client et tous les code dans le Server peuvent seulement marcher dans le serveur. Mais il y autre cartons et les fichiers dans ces cartons peuvent marcher dans client ou serveur. Donc on peut partager beaucoup de code qui nous aide écrire let utiliser le code mieux. Si le client et le serveur veulent utiliser la fonction la même, dans Meteor, on a besoin d’écrire une fois.

Ensuite, si on va exécuter la programmation Meteor, on peut entrer le carton d’abord et faire ça :
```
$ cd MyProject
```
Si on a utilisé les packages de Node, on a besoin de saisir le code, si non pas saisir :
```
$ Meteor npm install
```
Après on peut saisir :
```
$ Meteor
```
Le meteor peut connecter à MongoDB, ajouter les packages et autre choses. Si tous les choses sont bien, on peut saisir « http://localhost:3000 » sur le browser et voir le web.  


<h5 id="2.2">2.SEMANTIC-UI</h5>

Semanti-ui est un framework de UI qui peut faire le web afficher plus jolie. Peut-être ce n’est pas les travailler pour nous développeurs mais en stage c’est obligatoire pour nous. Comme le nom de cette framework, tous les CSSs sont sémantique. Par exemple, si on écrit « class= “ui two buttons” », il peut afficher deux boutons dans le même rang. Si on écrit « class= “ui red button” », il peut afficher un bouton rouge. C’est un framework sémantique donc si on peut connaître l’anglais on peut utiliser semantic-ui.

Semantic-ui n’est pas la partie de Meteor, donc on a besoin d’ajouter semantic-ui dans notre projet. Ici, je vous présente le management de package de Meteor. Si on va installer semantic-ui, on peut trouver les packages sur le website « Atmosphere » et il peut nous donner beaucoup de packages de semantic-ui pour Meteor. Bien sûr, s’il y a le package officiel, choisissez là. Le code de terminal est comme ça :
```
$ Meteor add semantic :ui
```
Si on va supprimer le package, seulement modifier « add » à « remove ». Si le package ajoute on peut utiliser les fonctions et les variables directement.
Tous les pages on a utilisé semantic-ui parce que c’est facile et sémantique. Si on modifie les fichiers de HTML écrit par autres personnes, ce n’est pas difficile de lire le code. On peut connaître les penses de développeurs et modifier les fichiers aisément.


<h5 id="2.3">3.AUTRE CHOSES</h5>

Il y a aussi beaucoup de bibliothèques de JavaScript.
	-underscore.JS
	Il est la bibliothèque de JavaScript pour résoudre de les data JSON(objet ou tableau). Il y a beaucoup de fonctions d’utiliser et c’est très expéditif pour nous de traiter les datas.
	-less
	C’est la même fonction que css mais dans le fichier de less, on peut écrire la logique. En fait, css est statique et less est dynamique.
	-reactive-dict
	C’est un plus important packages de Meteor.JS parce que il a fait le Meteor.JS web en temps réel. Si les datas de serveur sont changés, les datas de client et les pages de web sont changés le même temps. Je ne sais pas comment réaliser ça mais je sais comment utiliser cette package.
	-jQuery
	jQuery est une bibliothèque JavaScript libre et multiplateforme créée pour faciliter l'écriture de scripts côté client dans le code HTML des pages web3.
La bibliothèque contient notamment les fonctionnalités suivantes :
	* Parcours et modification du DOM (y compris le support des sélecteurs CSS 1 	à 3 et un support basique de XPath) ;
	* Événements ;
	* Effets visuels et animations ;
	* Manipulations des feuilles de style en cascade (ajout/suppression des 	classes, d'attributs…) ;
	* Ajax ;
	* Plugins ;
	* Utilitaires (version du navigateur web…).
	C’est très important parce que on a besoin de jQuery pour contrôler le DOM de HTML et si on utilise semantic-ui, jQuery est nécessaire.


<h4 id="3">III. LES MISSIONS</h4>

C’est un web application sur l’ordinateur, pad et portable par le technique cordovar de Meteor.JS. C’est un nouveau web donc nous stagiaires nécessitons faire le web début zéro. On doit créer le carton et donner la structure. Après, il y a beaucoup de missions de faire. Si quelqu’un a fini une mission, il peut choisir une nouvelle.

<h5 id="3.1">1.CREER LES PAGES ET REALISER LES CONTROLER</h5>

Pour moi, la première mission est créer la page de travaux. C’est une page de liste des travaux. Chaque travail a son fils des travaux concrets. Par exemple, il y un tableau de JSON :
```
Travaux =[
        // data 1
        {
            'name': "Aménagement et décoration",
            'type':"category",
            "children":[
                {
                    'name':"Montage meuble",
                    'type':"category"
                },
                {
                    'name':"Pose et fixation de tableau,patère, porte manteau",
                    'type':"category"
                },
                {
                    'name':"Pose et fixation miroir",
                    'type':"category"
                },
                {
                    'name':"Pose de tringle à rideau",
                    'type':"category"
                },
                {
                    'name':"Pose et remplacement d'équipement de porte",
                    'type':"category"
                }
        ]},
        //data 2
        {
            'name': "Rénovation & extension",
            'type':"category",
            "children":[
                {
                    'name':"Electricité",
                    'type':"category"
                },
                {
                    'name':"Revêtement muraux",
                    'type':"category"
                },
                {
                    'name':"Revêtement de sols",
                    'type':"category"
                },
                {
                    'name':"Climatisation ventilation chauffagiste",
                    'type':"category"
                },
                {
                    'name':"Plomberie",
                    'type':"category"
                },
                {
                    'name':"Cloisonnement & isolation phonique et thermique vertical",
                    'type':"category"
                },
                {
                    'name':"Menuiserie",
                    'type':"category"
                },
                {
                    'name':"Plafond  & isolation phonique et thermique honrizontal",
                    'type':"category"
                }
        ]},
        // data 3
        {
            'name': "Numérique",
            'type':"category",
            "children":[
                {
                    'name':"Installation HOME CINEMA",
                    'type':"category"
                },
                {
                    'name':"Pose support mural pour TV",
                    'type':"category"
                },
                {
                    'name':"Installation HIFI",
                    'type':"category"
                }
        ]},
        // data 4
        {
            'name': "Jardin et extérieur",
            'type':"category",
            "children":[
                {
                    'name':"Entretien",
                    'type':"category"
                },
                {
                    'name':"Neuf",
                    'type':"category"
                }
        ]},
        // data 5
        {
            'name': "Manutention & évacuation",
            'type':"category",
            "children":[
                {
                    'name':"Déménagment",
                    'type':"category"
                },
                {
                    'name':"Curage",
                    'type':"category"
                }
        ]},
        // data 6
        {
            'name': "Urgence",
            'type':"category",
            "children":[
                {
                    'name':"Porte",
                    'type':"category"
                },
                {
                    'name':"Fuite",
                    'type':"category"
                }
        ]},
    ];
```  
C’est très long mais claire que j’ai besoin de créer le menu de ce tableau. D’abord, le buttons du menu sont :

* Rénovation & extension
* Aménagement et décoration
* Numérique
* Jardin et extérieur
* Manutention & évacuation
* Urgence

Si je clique le bouton « Rénovation & extension », il doit afficher le menu du fils qui sont les boutons 

* Montage meuble
* Pose et fixation de tableau, patère, porte manteau
* Pose et fixation miroir
* Pose de tringle à rideau
* Pose et remplacement d'équipement de porte

En fait, si cliquez le bouton il y a deux occasions. Si la catégorie a fils il peut afficher le menu du fils sinon il peut accès à la page de l’estimation. C’est facile de réaliser pour moi mais c’est utilisée sur web page donc je dois faire ça par les fonctions de Blaze Template. Si la catégorie a le fils et il a besoin d’afficher le menu je peux utiliser l’circulation comme ça :

```
{{site.rap_1}}
```
ou
```
{{site.rap_2}}
```

Le paramètre catégorie est défini par le Template helpers dans le ficher JavaScript. Mais l’circulation est dans le fichier HTML. Si on a défini un Template, on peut le donner un nom. Les paramètres de Template sont définis dans le fichier JavaScript et ils peuvent être lus et utilisés dans le Template le même nom dans le fichier HTML. En fait, ajoutez la logique dans le HTML fichier est bien et facile de réaliser le View de MVC.

![avatar](/images/blogs/2016-10-05-02.png)

Ça c’est le parti du menu maintenant et il a été changé par beaucoup de fois. Quand je fais ça, c’est très simple et pas photos sur les boutons.

<h5 id="3.2">2.PACKAGE DE DBURLES : GOOGLE-MAPS</h5>

Je pense que j’ai fait un exemple du web par Google-Maps donc j’ai la mission sur ça. Cette package est très base qu’il contient les base APIs et comment afficher la carte par Google-Maps. C’est très bien et facile d’utiliser. Mais avant que on préparer utiliser cette package, on doit demander la clé de Google-Maps API sur le web du Google. Si on n’a pas de la clé, la carte ne peut pas afficher normal.

On dépose la clé dans le fichier startup et cette clé aussi fonctionne des APIs de Places.

En fait, on peut entrer la page de Google Maps développer et choisir les APIs de JavaScript. Mais si on fait ça, c’est très compliquer que le package. Par le package, on peut créer la carte par les paramètres définies dans le fichier de JavaScript comme les fichiers Meteor.JS. Il aussi utilise Template et on peut utiliser les APIs directement dans Meteor.JS.

![avatar](/images/blogs/2016-10-05-03.png)

C’est est la carte de worker. Il affiche le rayon du domaine où il peut donner les services. Le marker et the cercle sont peint par les APIs. Selon les situations, je choisi l’API de cette package ou l’API par Google-Maps directement.

<h5 id="3.3">3.GOOGLE MAPS API DE PLACES</h5>

Pour saisir les adresses automatiques, on doit utiliser les APIs de Places par Google-Maps. Il a nous donné beaucoup de méthodes et fonctions de choisir. On a choisi auto complétion.

![avatar](/images/blogs/2016-10-05-04.png)

Comme ça, si on a saisi le nombre ou alphabet, il peut afficher les adresses correspondant que votre importation. Pour France, il peut nous donner le numéro et nom de Rue, Avenue…, le code postal, le nom de la ville, le nom du département, le nom de la région. Par les informations, c’est facile de nous de trouver l’adresse.

Mais il seulement fonctionner sur les adresses du web de https. A ce moment, chrome peut utiliser ça par http mais safari ne peut pas.

![avatar](/images/blogs/2016-10-05-05.png)

Le résultat est comme ça, mais par default, tous les informations afficher dans l’input de l’adresse. Mais on peut utiliser le fonction getPlace() pour obtenir tous les informations comme le département, le pays etc.
Le code de réaliser l’auto complétion est
```
	let input        = document.getElementById('street');
  let autocomplete = new google.maps.places.Autocomplete(input);
```
Est si l’adresse est changée, on peut fournir les inputs de rue, code postale etc. Donc on a besoin de addListener pour faire ça et après on peut utiliser getPlace() pour obtenir l’information que on a besoin de.

<h5 id="3.4">4.FICHIER DEPOSER PACKAGE DE VSIVSI/METEOR-FILE-COLLECTION</h5>

Je pense que ça c’est la plus difficile mission de moi dans le stage. C’est un package de file-colletion par Grid Files sur MongoDB. Le base de cette méthode est on peut déposer les fichiers par beaucoup de parties. Parce que le single fichier dans le MongoDB est maximum 1m donc si on veut déposer le fichier plus grand que 1m, on peut dévider les fichiers a beaucoup de parties et déposer tous les parties. Grid Files a réaliser cette pense et cette package fait Grid Files fonctionner dans Meteor.JS.

J’ai créé deux modules, un est photo, un est fichier. Je suis obliqué de dévider les deux types de fichiers parce que les opérations ne sont pas même. Il y a beaucoup d’exemples dans la page de vsivsi/meteor-file-collection sur GitHub et l’auteur aussi nous donner l’exemple de projet de Meteor.JS par CoffeeScript qui est en fait le même que JavaScript.

D’abord, cette package nous aide de créer une JSON objet de fichier qui contient beaucoup de choses comme md5, nom de fichier etc. Pour vérifier le fichier uniquement, c’est mieux de choisir md5 pour lire le fichier. En fait, l’exemple d’auteur aussi utilise md5. C’est la connaissance de cryptographie !

Après l’objet est créé, le fichier peut être déposé dans le MongoDB de serveur. Donc si on utilise RonbomMongo on aide voir la base de données, il y a trois collections de photo ou fichiers. Un est les informations de fichier, un est les data de fichier, mais l’autre je ne sais pas est quoi.

Ce n’est pas facile d’utiliser parce que en développement, il y a beaucoup d’erreurs concernant les fichiers de déposer.

<h5 id="3.5">5.SITEMAP</h5>

Avant le stage, je ne sais pas qui est sitemap. C’est seulement pour les web de rechercher comme Google. Le développeur de web peut donner beaucoup de urls du web et déposer les urls dans un fichier, c’est facile des utilisateurs de Google ou autres webs de rechercher trouver ce web facilement. La clé peut été trouvé plus commodément.

![avatar](/images/blogs/2016-10-05-06.png)

C’est la page de sitemap, le type est XML. En fait, c’est la liste de urls et le date de mise à jour.

<h4 id="4">IV. LES CONNAISSANCES APPRIS EN STAGE</h4>

A ce moment, c’est aussi la période de stage pour moi parce que le stage est jusqu’à le 10, novembre. En stage j’ai appris beaucoup. Avant le stage, je peux écrire le code PHP ou Java avec Oracle ou MySQL et je peux aussi utiliser JavaScript et HTML de réaliser les pages statiques. Je peux écrire la programmation par Socket(TCP/IP), par HTTP ou FTP mais je ne sais pas comment utiliser tous les connaissances de réaliser une application du web.

Pour faire le stage, j’ai lu beaucoup de documents comme RESTful, webSocket, router, Node.JS etc. Et en stage, j’ai appris underscore qui est une bibliothèque de JavaScript et MongoDB qui est la base de données NoSQL. Aujourd’hui, je pense que j’ai la capacité de créer un web moi-même. En fait, j’ai fait le web et il a partagé sur GitHub.

C’est la liste de connaissances qui j’ai appris pendant le stage :
- Meteor.JS
- Node.JS
- Semantic :UI
- jQuery
- underscore
- MongoDB
- JSON data
- Grid Files
- Transmission d’email
- Google Maps API par JavaScript
Aussi, j’ai appris beaucoup de choses technique et comment nettoyer le code. Je vais continuer mon stage et apprendre plus.

<h4 id="5">V. CONCLUSION</h4>

Pour moi, c’est la première fois de faire le développement du web dans une société. Et c’est le langage JavaScript qui n’est pas le même que le langage que j’ai utilisé avant. Il n’y a pas class mais il est objet ou tableau en JSON. C’est un autre type de langage donc j’ai besoin d’apprendre beaucoup de nouveaux connaissances.

Avant le stage, pour apprendre Meteor.JS, j’ai déjà fait un petit web qui seulement réaliser la fonction de trouver les personnes par ses profils. C’est le web application d’une page mais j’ai utilisé Meteor.JS, semantic-ui et Google Maps API. Après j’ai fait le simple web, je pensais que c’est très facile et Meteor.JS est commode de créer un web que autres frameworks. Mais quand j’ai fait le stage, je trouvais que ce n’est pas possible, Meteor.JS est aussi difficile et il peut m’apporter beaucoup de problèmes du web développement.

Le stage m’aide beaucoup de comment faire le développement du web. Quelle méthode est bien et quel type de chercher le data en base de données est sécuritaire. Ce n’est pas le même que le projet à l’école. On doit considérer plus parce que c’est le web commercial.

Quand le web programmation est plus grand, les problèmes sont plus. Donc chaque jour on est obliqué de résoudre les problèmes. C’est le travail pendant quelque mois pas seulement quelques semaines. Parfois, le problème est petit mais il est très difficile de trouver ou est le problème.

En somme c’est une bonne chance pour moi de participer un projet commercial qui m’a fait connaître comment travailler dans une équipe et comment faire le développement du web.
