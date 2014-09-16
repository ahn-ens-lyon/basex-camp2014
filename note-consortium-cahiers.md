
SynopX
------

Synopsx est un système de publication léger, entièrement fondé sur des technologies XML à partir de la base de données XML native BaseX. Initié par l'Atelier des Humanités Numériques de Lyon (AHN), le projet est développé comme logiciel libre par une équipe de plusieurs contributeurs issus du monde académique. Le logiciel libre et open source est basé sur les fonctionnalités RESTXQ implémentées par BaseX. 

Entrepôt github du projet :
https://github.com/ahn-ens-lyon/synopsx

Dans son état actuel, le logiciel permet :
- une publication personnalisée de sources textuelles XML-TEI,
- une publication d'entrepôt OAI-PMH,
- une articulation entre des sources EAD et XML-TEI
- de disposer d'un moteur de recherche sommaire

Le code du logiciel se caractérise par son extrême concision et son caractère modulaire. Il est donc très aisé de se l'approprier et de l'adapter à ses propres besoins. Ce logiciel, qui a été présenté aux journées Cahier au début du mois de juillet est déjà en production pour différentes applications web de l'ENS Lyon. Plusieurs partenaires membres du consortium Cahier lyonnais et parisiens (ANR Ampère, et Projet des Guides de Paris notamment) participent déjà au projet.


Mutualisations possibles autour de SynopsX
------

Compte-tenu des coûts liés à la réalisation d'une application de publication web de sources XML-TEI, SynopX permet d'envisager la réalisation des développements en interne pour la partie architecture de données de l'application.

La base de données XML native BaseX permet en outre de disposer d'une implémentation du standard XQuery Full-text qui autorise la construction de moteurs de recherche plein texte sans avoir recours à des systèmes dédiés comme Solr ou Lucenne ce qui réduit considérablement la complexité de l'application et sa maintenance.

RESTXQ est une standardisation prometteuse qui, outre son élégance, permet de rédiger des applications web de façon entièrement déclarative avec une extrême concision. Cette simplicité garantie des modifications aisées et offre beaucoup d’autonomie dans la réalisation du projet notamment pour expérimenter divers dispositifs de publication ou faire des modifications.


Le travail autour de SynopX offre un cadre de mutualisation sur les aspects communs à toute édition de sources XML-TEI en évitant de reproduire les mêmes développements chacun pour ses propres besoins. Cette économie de temps de développement permet de se consacrer aux aspects spécifiques de son édition.

Compte-tenu de la légèreté du code de SynopsX, et du fait que les besoins en matière de publication de sources XML-TEI sont très généralement comparables, il est très facile de se l'approprier pour construire son application. Un tel choix présenterait plusieurs avantages :

1° il permet de bénéficier de développements déjà réalisés 
2° il permet d'inscrire le projet dans un cadre collectif très souple qui permet d'améliorer la qualité du code produit et la pertinence des choix de développements
3° il permet de bénéficier d'un logiciel qui sera également utilisé par d'autres ce qui lui garantie une meilleure maintenabilité dans le temps


Objet de la demande au Consortium cahier
------

L'équipe qui travaille sur le développement de SynopsX organise une semaine de co-Working à Konstanz avec les développeurs de BaseX en novembre 2014. Plutôt qu'une stricte formation avancée, cette semaine de co-working sera l'occasion de travailler en commun sur les développements de SynopsX afin d'améliorer l'organisation du code et l'architecture générale du projet. Plusieurs développements seront réalisés à cette occasion pour faciliter la prise en main du logiciel pour la création de nouveaux projets de publication XML-TEI.

L'organisation de cette semaine de co-working implique le financement des formateurs et la prise en charge des frais de transports et de résidence à l'université de Konstanz. On sollicite le consortium Cahier pour une participation aux frais de transports et d'hébergement des membres du consortium pour cette formation. Compte-tenu de l'intérêt de SynopsX pour d'autres membres du consortium, l'équipe de développement de SynopsX se propose d'organiser une formation à destination des ses membres.


BaseX et les bases de données XML natives
------

### BaseX

BaseX est un logiciel de base de données XML natif développée depuis 2006 par l'université de Constance. C'est un logiciel libre qui dispose d'une importante communauté d'utilisateurs tant dans le domaine académique que commercial. Avec le logiciel eXist, BaseX est la principale base de données XML native libre et open source du marché. Il existe également des bases de données XML natives commerciale, le leader dans ce domaine étant MarkLogic.

Les bases de données XML natives permettent de stocker et d'indexer des documents XML afin de les manipuler, les mettre à jour ou réaliser diverses transformations. Ces systèmes sont généralement conçus pour travailler avec des fichiers XML sans transformation préalable, ceux-ci s'insèrent donc bien dans un cadre de travail où l'on produit des sources dans un format XML. Ils implémentent généralement le langage de manipulation de données et de requête XQuery développé par le W3C qui est un langage de programmation fonctionnel Turing complet.

BaseX et eXist présentent des fonctionnalités similaires aux logiciels concurrents. Outre des performances plus importantes, par rapport à eXist, BaseX présente l'avantage d'avoir implémenté plus complètement le standard du W3C XQuery et en particulier son extension XQuery full-text qui permet la construction de moteur de recherche plein-texte. Le logiciel BaseX offre également une très bonne implémentation de RESTXQ, une extension XQuery qui permet la création d'applications REST (REpresentational State Transfer).


### Construction d'applications avec des bases de données XML native

L'aptitude des systèmes de bases de données XML natifs à manipuler des documents XML permet d'envisager leur utilisation pour remplacer les systèmes de base de données relationnelles dans le cadre de la production d'applications web dynamique. Dans un environnement LAMP (Linux, Apache, MySql, PHP), ils peuvent par exemple judicieusement remplacer MySql. Cependant ces systèmes étant généralement développés en Java, ils impliquent de disposer d'un environnement adapté pour les déployer.

La plupart des systèmes de bases de données XML natifs proposent des fonctionnalités de type serveur qui permettent la construction d'applications web entièrement rédigées en XQuery. De ce point de vue, ils constituent souvent des solutions simples et adaptées pour la publications de sources XML lorsque l'on maîtrise les langages de la famille XML (XQuery, XPath, XSLT). Une solution de ce type permettant ainsi de se passer complètement de tout autre langage de programmation. C'est ce qui explique en grande partie la faveur actuelle de ces systèmes pour la publication de données XML-TEI.

### RestXQ

En 2012, Adam Retter a proposé une normalisation concernant l'écriture d'applications web de type REST (c'est à dire fondées sur les contraintes de l'environnement web au sens de la thèse de Roy Fielding) en utilisant des annotations XQuery. Bien qu'elle soit récente, cette proposition de spécification a déjà été implémentée par les principaux acteurs du marché. Elle permet de proposer une manière standardisée de décrire des applications web en les rendant portable d'une application à l'autre.

RESTXQ fournit donc une solution simple et élégante de publication web qui présente l'avantage d'être entièrement basée sur des standardisations. 

