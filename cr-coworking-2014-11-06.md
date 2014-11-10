cr corworing 06 novembre 2014

Si projet spécifique met dans webapp
Sinon dans repo car pas de pb de chemins

Actuellement place tout dans synopsx.

Lors de l'importation d'une base de données, il est possible de définir la langue d'importation, la stemmatisation, définir la sensibilité à la case et les diacritiques, ou les mots vides (stopword).

Tous les mots sont tokenisés sous forme de binaires. Mais des fonctions xquery sont disponibles pour accéder aux données directement.

Les options par défauts sans stemming, case sensitive et diacritics.

Après l'importation, présente des premières informations sur les entrées d'index.

Lorsque réalise une requête
Chercher une chaîne dans le texte :
//*[text() contains text 'paris']

Ce qui est intéressant c'est que la requête est optimisée par le moteur.

/descendant-or-self::node()/child::*
optimisée
db:open-pre("gdpTei",0)/descendant::*

En revanche ne peut pas optimiser //*[1]
Il n'est généralement pas nécessaire de réécrire le path. à moins qu'utilise des bases différentes.

Au moyen de l'index, la requête est exécutée 100 fois plus vite (ex drop l'index pour voir). Java optimise aussi sa machine virtuelle, généralement va plus vite.

Requête:
let $db := db:open('gdpTei') return $db/descendant::*[text() contains text 'Lyon']
Requête Optimisée:
ft:search("gdpTei", "Lyon")/parent::*

Autre exemple employé dans une fonction

declare function local:query(
  $db as xs:string,
  $word as xs:string
) {
  db:open($db)//*[text() contains text { $word }]
};
local:query('gdpTei', ('Paris'))


voir l'article sur la recherche full text et fuzzy

declare option db:lserror '1';
'sea' contains text 'see' using fuzzy

Fonctionne bien aussi si travaille sur plusieurs langues différentes.
Intéressant pour des langues où des comparaisons morphologiques possibles

ft:search('gdpTei', 'Lyon')/parent::*

Plusieurs algorithmes de calculs possibles pour analyser la distance du texte.


Même utilisation pour analyser le type d'erreur
db:openn()
Erreur:
Arrêté à /Users/emmanuelchateau/Sites/synopsx/webapp/restxq/fichier, 1/10:
[XPST0017] Unknown function 'db:openn'; similar: 'db:open'.
Requête:
db:openn()



Lors que dispose de plusieurs base s

declare function local:query(
  $db as xs:string,
  $word as xs:string
) {
  db:open($db)//*[text() contains text { $word }]
};
local:query('gdpTei', ('Paris'))


Factorisation des modes modes :

declare function local:query(
  $db as xs:string,
  $word as xs:string
) {
  let $ftindex := db:info($db)//ftindex='true'
  let $options := map{
      'mode': 'all words',
      'fuzzy': true()
      }
  return if($ftindex) then (
    ft:search($db, $word, $options)
  ) else (
    db:open($db)//*[ft:contains($db, $word, $options)]
  )
};
(: ouvre deux bases :)
for $db in ('gdpTei', 'users')
return local:query($db, ('lion'))

Lorsque l'on a du contenu mixte problème pour traiter du texte en full-text, en éliminant les balises.
Fonctionne avec contains(), et non pas avec les fonctions full-text.

Problème de mise à jour incrémentielle.
Support des wildcard et des fuzzy queries
par contre pas de support des incrémential updates

Capable de prendre les références aux éléments parents et ancêtres. surppot de match mais sans optimisation.
cf. issue github 2012 full-text index

ft:extract(db:open('gdpTei')//*
[text() contains text 'Paris'], 'HITHITHIT')

ft:mark(db:open('gdpTei')//*
[text() contains text 'Paris'], 'HITHITHIT')

ft:mark(db:open('gdpTei')//*
[. contains text 'Paris'], 'HITHITHIT')

autre exemple

let $db := 'gdpTei'
let $terms := ('lyon')

let $hits := <hits>{
  ft:extract(db:open($db)//*
[text() contains text 'lyon'], 'hit')
}</hits>
return $hits update (
  for $hit in .//hit
  return insert node attribute x { 'bla!' } into $hit
)

Limitations

let $db := 'gdpTei'
let $terms := ('lyon')

let $hits := db:open($db)//*
[text() contains text { $terms }]
for $i in 1 to 5
return ft:extract($hits, 'hits')

Il n'y a pas de moyen de stocker un résultat intermédiaire pour ensuite réaliser une extraction sur l'ensemble rassemblé.
Travail en cours.

Dans ce cas, il vaut mieux réécrire la recherche, même si moins joli :

let $db := 'gdpTei'
let $terms := ('lyon')

let $hits := db:open($db)//*
[text() contains text { $terms }]
for $i in 1 to 5
return ft:extract(
  [text() contains text { $terms }], 'hits')

Lorsque l'on utilise les fonctions par défaut de XPath, il n'y a pas d'utilisation des fonctions optimisées (starts-with(), etc.). Pour les requêtes exactes les index mieux. contains() très difficile à accélérer dans un système d'indexation.

contains('apple', 'pple')
pas possible d'augmenter la vitesse avec un index car des lettres dans tous les sens.


apple' contains text 'ap.*' using wildcards
là plus possible

let $user-query := 'ap im'
let $query := ft=tokenize($user-query) !
  (. || '.*')
let $input :=
<x>
  <text>apfel im kuchen</text>
  <text>apfel am baum</text>
</x>
for $text in $input/text
return $text contains text { $query }
all words using wildcards


autre exemple :

let $user-query := 'apfe im'
let $query := ft=tokenize($user-query) !
  (
    if(string-length(.) > 3) then (. || '.*') else .
  )
let $input :=
<x>
  <text>apfel im kuchen</text>
  <text>apfel am baum</text>
</x>
for $text in $input/text
return $text contains text { $query }
all words using wildcards

Quand commence à avoir des données trop volumineuses, il peut s'avérer utile de disposer de deux bases de données. L'une pour l'index, l'autre pour le reste.
Par exemple dans le NY peut s'avérer que veuille rechercher seulement les titres et rien d'autres.


Création d'une base pour l'indexation

db:create(
  'titresTei',
  <titles>{
    for $title in db:open('gdpTei')//head
    return $title
  }</titles>,
  'titresTei.xml'
)

Pas un problème géréralement d'itérer dbopen dans la requête.
La base n'est ouverte qu'une fois, cela fait partie de la sémantique de xquery

db:open('gdp')[1] is
db:open('gdp')[1]

alors fait référencedans la base = true
Un principe d'identité

<x/> is <x/>
false

let $x := <x/>
let $xx :=
for $i in 1 to 5
return $x
return $xx[1] is $xx[2]

alors true

En revanche si utile input pas de pb, toujours la même référence.

Utiliser db:open-pre() pour les bases non susceptibles de changer
et db:open-id() pour celles susceptibles d'être modifiées.


Dans bien des cas mieux vaut se reposer sur l'optimiseur de requête. Dans bien des cas // plus rapide que de décider quel est le parent. Pas de différences en fonction de la réalité.
