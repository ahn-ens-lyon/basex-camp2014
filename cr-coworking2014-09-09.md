CR Coworking, 9 septembre 2014
-----------

## Financement de la formation Synopsx

Travail sur le budget de la semaine à konstanz
3500 euros de l'ENS
Il manquerait 500
Hébergement Ibis, 6 personnes 6 nuits = moins de 2000 euros. L'hébergement dans le privé peut poser des difficultés pour la facturation.

Demander à Cahiers une participation en leur proposant d'animer une formation l'année prochaine à destination des membres du consortium.

Difficultés pour faire comprendre l'intérêt du projet réglées au sein du projet des Guides de Paris
Philippe recruté pour travailler sur la plateforme à l'ANR Ampère.

--> Prendre contact avec le Labex pour le financement
--> Idem ANR Ampère
--> Idem Laurence Ragot du consortium Cahiers.
Faire le point à la fin de la semaine


## Tour de table

Tous les développements sont maintenant en principe dans Github.
Il y a actuellement plusieurs branches dans l'entrepôt :
- la branche master la version stable
- une branche head qui viendra alimenter la branche master
- branches par projets qui dérivent de la branche de développement

Adopter l'organisation distribuée proposée par ce tutoriel sur les workflow github
https://www.atlassian.com/fr/git/workflows

Emmanuel
Travail sur les interactions avec la base pour la création des projets en utilisant REST. Bien avancé mais quelques blocages.
Par ailleurs, a pas mal exploré la question du templating.
Trois pistes pour la formation :
- architecture du projet, de l'application, performance, etc.
- travail sur les en-têtes TEI d'un corpus
- outil d'indexation
- moteur de recherche full-text

Philippe aurait besoin de pouvoir faire le point sur le code. On propose d'organiser une séance de documentation.
Parvenir à organiser le code de manière pouvoir travailler en commun et mutualiser.

Modules de fonctions par langage, ou fonctions pour lister des items qui peuvent être mutualisés. 

Séverine a beaucoup réfléchi et échangé sur des applications possibles pour Triangle. Mais pas encore travaillé sur le code. Voudrait faire la même chose que sur hyperprince, mais aussi travailler sur le lexique et une application.
Suivre les directions proposées par le LDI creasciences http://www.crealscience.fr
Équipe très avancée sur l'utilisation de BaseX qui a développé des outils lexicaux. Pour son projet, des perspectives lexicales.

Sylvain du Larhra : spécificité de travailler avec un SGBD relationnel dans lequel stocke pas mal de chose. Un module pour travailler avec.
Du point de vue de l'organisation comment mieux séparer le codage entre html et le reste. Logique MVC.

Utilisation de Xquery pour traiter récupérer l'arbre résultat, mise en forme ensuite plus simple avec XSLT. Séparer la logique des données de la mise en forme.
Prévoir une grosse journée de travail sur les utilisations avancées de BaseX.

Pierre-Yves essaye de rattraper les wagons, aimerait avoir un aperçu des projets pour identifier ce qui est fait et les manques éventuels. A été confronté à des problèmes de mise à jour de BaseX depuis les sources. Voir s'il existe des choses pour la mise à jour automatique.

Travail avec Maud en doublon sur les projets pensées classique. Utilisation de Synopsx, pour le moment du mal à entrer dans le système et attends beaucoup de la documentation. Recherche une sorte de templating comme avec SPIP.

Reconstitution des index au moment de la mise à jour de la base de données possible avec la nouvelle version de BaseX. Optimisation de requêtes.

Jean-Philippe ajouterait besoin de backoffice. Travailler sur un backoffice. Comment faire fonctionner des XForms pour éditer à travers les formulaires pour éditer les bases de données de configuration. Tirer parti des logiques REST.
Gestion des utilisateurs et des droits.

Maud même besoins, organisation du code templating. Ajouterait à la gestion des utilisateurs, la gestion de session. Avoir une notion de pannier et de session.
Super idée que le fil rouge de la semaine soit organisé autour de la construction d'un backoffice et architecture de l'application.

Travailler sur le moteur de l'application hypermédia Synopsx : 
- architecture de l'application (backoffice, gestion des bases de projet, gestion des utilisateurs utilisateurs)
- modularisation et organisation du code (bonnes pratiques)
- templating

Exposés technique en début de journée
Définir 5 points

Jour 1 : REST utilisation avancée des paramètres HTTP, redirect, négociation de contenu
Jour 2 : gestion utilisateurs
Jour 3 : index et branchements externes
Jour 4 : connexion bdd

? : organisation et modularisation du code
? : templating

Prévoir une 1/2 journée sur des pistes d'appel d'offre ou de travail en commun


Fil rouge de la semaine :
- Best practices in code organisation of a webapp : 
1) Organizing code in xqm modules / Webapp / Repo...
2) Templating, splitting queries/serialization
3) BaseX admin : code overview / upgrading automatization / Versioning of the xqm files, versioning of the xml data
4) User management : connecting with an openid, LDAP, etc.


- Advanced restxq : redirect, content negociation...
- User sessions : for example, adding a "basket" feature to a webapp
- Indexes, connecting to lexical tools
- Connecting to relational DB, mixing XML and relational data
