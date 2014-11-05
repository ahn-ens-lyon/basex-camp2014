# cr coworking-2014-11-05

Pour la localisation des fichiers, voir File Module
file:parent($path) pour localiser le chemin

Pour le deployement
bin/
lib/
basex.jar
+doc

Distribuer Synopsx avec le `.basex` et le `.basexhome` dans le répertoire

Habituellement travaillent avec des instances multiples car BaseX est plutôt léger et donc ce n'est pas un inconvénient et cela rend les choses plus flexibles.

http://docs.basex.org/wiki/Configuration

À terme, il n'y aura plus de gui, l'ensemble devra passer en web pour toute l'administration serveur.
Le gui est plutôt destiné à développer localement ou bien explorer les données.

Un module Database Administration doit normalement être publié avec la version 8, probablement dans webapp.

Utilisation de Session à partir du module de Session prévu par BaseX
web:check() dans global qui détermine la session en cours
web.xqm où traite les logiques des sessions à l'aide du module Session.

redirect renvoyé au client et le serveur choisit
rest:forward ne met pas nouvelle adresse pour continuer des redirections sans nouvelles requêtes.
Utilisent habituellement redirect car c'est plus conforme à la logique REST.

Gestion des erreurs
des extensions ajoutées à RESTXQ
Lorsque quelqu'un n'est pas autorisé à entrer, une fonction login-error

Fonction qui utilise annotation %rest:error http://docs.basex.org/wiki/RESTXQ#XQuery_Errors
Qui permet de renvoyer un message à l'utilisateur.

Précédemment traitaient cela avec redirect()
Aujourd'hui voudraient ajouter des annotations comme %sec:requires()
Pas totalement idéal car implique de placer le web:check() à chaque fonction, et les oublie parfois. Mais elles peuvent prendre un paramêtre comme `admin`, etc. web:check('admin')

Comme ces problèmes se présentent dans de nombreux projets de manière récurente, envisagent donc de les déplacer vers le cœur de l'application par l'intermédiaire d'une annotation.

Généralement redirect pour faire des XQuery update compte tenu de la sémantique de XQuery update.


Chemins
deux options soit considère le répertoire de travail soit relatif à la localisation du fichier.
Utiliser à l'avenir file:base-dir() pour définir un répertoire de démarage.
Pour construire chemin calculé
file:parent(static-base-uri......) || chemin


N'utiliserait pas de redirect.
Possibilité d'ajouter des options de sorties comme annotation statiques.
Dans ce cas ce que peut faire
créer des éléments réponses.

utiliser des Response element
avec cela évitera alors de multiplier les annotations.


Majuscules pour l'espace de nom des fonctions qui n'appartiennent pas au cœur de BaseX
Request:header('Accept') pour récupérer les valeurs d'entête HTTP.
Tokeniser les chaînes.
écrire la loqique.

1 = (6 to 5)
true

() != (1 to 5)
false

() = ()
false

= teste toute les combinaisons


opérateur map !
prend chaque séquence et fait autre chose avec
! . ramène seulement la chaîne
...

prof:trace($variable) pour afficher les variables
prof:dump($variable) id mais...

prof:variable() rend les différentes variables disponibles dans le code


Problème de deux chemins RESTXQ identiques, l'un par un motif l'autre déclaré en dur.
Celui qui sera utilisé, le plus spécifique.
Pas spécifié in SAXJS


# Gestion des utilisateurs pour le moment de dba seulement les utilisateurs de l'application

Dans le projet Klett, traitent touts les utilisateurs du système séparément dans une base de données qui stocke les rôles, les mots de passe, etc.

Chaque utilisateur dispose de droits sur certains vocabulaires.

Dans le système, une base de données par vocabulaires.

_catalogue dans lequel stockent les utilisateurs, la base XML contient users.xml, titles.xml, inflections.xml

declare option output:item-separator

dans admin/
plusieurs répertoires qui permettent de classer les domaines
filters/
titles/
users/

----

pour créer base
redirect comme fonction avec %updating

nouvelle fonction mixupdates dans version 8

pour les messages d'interface utiliser dans <rest:redirect>tei?1</rest:redirect>
chemin avec n°
Reprendre le N° dans les paramètres rest et délivrer message

mieux vaut passer les messages d'interface dans l'url, car on ne peut pas faire redirect avec POST. Pour le moment seulement possible d'y accéder en get.


rest:error annotation
mais aussi

P
