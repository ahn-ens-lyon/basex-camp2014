# cr co-working 4 novembre 2014

## Présentation de la logique de l'application

L'application peut gérer différentes bases de données pour la publication qui correspondent à des chemins différents définis au moyen d'un map.

Une fonction main appelle le système. Par ailleurs un héritage pour proposer une gestion par défaut des projets. Chaque projet nécessite un fichier de configuration qui indique l'héritage.
Le module ahncommons dans cet héritage propose une structure par défaut.
<configuration>
  <!-- héritage -->
  <!-- nom du module à employer -->
</configuration>

L'héritage est géré dans la fonction lookup.

Plusieurs inconvénients, héritage à un seul niveau et mélange du code dans les fonctions.

---

Leurs premiers projets réalisés exactement de la même manière avec le code mélangé avec les fonctions.
Aujourd'hui en train de développer un système où des fichiers HTML qui sont ensuite rendu côté client en JavaScript avec les données traitées en XQuery.

Pas certain qu'il y ait une manière générique pertinente de le faire seulement en XQuery.

Actuellement ce que font :
un module de template qui contient du code HTML et auquel passe des paramètres.


```xquery
declare function template:wrap($content){
  <html>
  <title>{$content}</title>
  </html>
};

declare
  %rest:path("/wrapped")
  %rest:query-param("name", "{$name}", "anonymous friend")
  %ouput:method("html")
  function _:hello-wrapped{

};
```

Tout ce qui est dans RESTXQ sera dans le serveur REST. Ce qui est dans REPO est en revanche disponible en ligne de commande.

éditeur webstorm

synopsx.xqm supposé réaliser toutes les tâches, mais oblige à déclarer tous les projets à cet endroits donc insatisfaisant.
En fonctionnant avec ce module, aura besoin de le déclarer. D'autres outils pourraient écrire ce fichier pour vous. Car pour le moment pas de fonctions pour changer le contenu dynamiquement.

Rédigé une fonction qui charge un fichier HTML depuis le disque
Facile de charger fichier 2, etc. plus qu'à remplacer le contenu


Proposent une solution avec simple XQuery update pour modifier le contenu d'une page xhtml.

Pour la récursion, proposent de placer les documents dans un répertoire au même niveau que repo et de gérer les projets comme des variables. Alors l'héritage ne serait qu'à un seul niveau.

voir comment employer la fonction serialize sur une fonction qui n'est pas restxq.

Voir l'exemple dans le BaseX https://github.com/BaseXdb/basex-contrib


## Moustache

Jamais encore utilisé Moustache notamment car pas du XML. Présente des contenus avec des marqueurs que remplace par du XML. Mais me semble pas pertinent.


## AngularJS

XML modèle directement connecté avec XForms aux input, c'est à peu près la même chose avec AngularJS au niveau des modèles de données.

Vous allez donc avoir un objet JSON dans le browser qui sera rendu directement par le browser comme vous l'avez choisi.

Exemple Hello World
JSON ne permet pas de rendre du contenu mixte, mais cette limitation concernait déjà XForm. Passés à AngularJS car beaucoup plus flexibles.

ng-model
ng-bind
ng-disabled

AngularJS un framework qui permet de définir une structure d'application avec des chemins et des contrôleurs, et pour chaque possible de définir des directives avec des web components.

Permet donc d'utiliser des composants réutilisables sur l'ensemble de l'application.

XForms un très bon concept, mais pas de drag and drop, pas de popup, etc. Seulement l'implémentation d'Alain Coutures en libre.

http://www.agencexml.com/xsltforms
http://www.betterform.de/en/index.html (marche moins bien que xsltforms)

----

Définir une manière de traiter les uri pour les projets multiples


Dans repo modules les fonctions sont placées dans l'espace de nom par défaut

repo/
-- models/ les fonctions qui construisent la structure
-- views/ les fonctions qui appellent les vues


# Question

Q{default-ns}
Comment sérialiser avec Qname

Faire des redirect pour dire quand le header, fait cela, etc.
