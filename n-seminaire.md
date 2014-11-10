title: synopsxSemDBIS2014
description: presentation synopsx Séminaire DBIS, co-working BaseX
theme: theme/remark-dark.css
name: inverse
layout: true
class: inverse

---

name: index
class: center middle

# SynopsX
[DBIS seminar, 4 november 2014]

.footnote[https://github.com/ahn-ens-lyon/synopsx]

---

# instrumented corpus

### .red[1.] expose / publish

### .red[2.] explore / visualize
<!--  -->
### .red[3.] enrich / link

???

SynopsX is a collective project whose aim is to propose a web application built on BaseX to easily expose and publish XML textual sources and data (mostly encoded in TEI http://tei-c.org/).

Initiated by the Atelier des Humanités Numériques (Digital Humanities Workshop) from École Normale Supérieure in Lyon, SynopsX gathers various french projects in the fields of history and literary studies.

The 6 people here to participate a coworking with BaseX are all engaged in different projects but all share the same conception about what should be what we call an "instrumented corpus" :

Saying that, we mean :
- corpus you can more than publish, but expose on the web
- giving to the researcher or to visitors tools to explore and visualise the datas
- and text distribution that allow you to enrich and link the data on the Linked Open Data

---
template: inverse
class: center middle

# .red[1.] expose/publish

---
background-image: url(backgroundPastilles.gif)
layout: false

# TEI as a common model

```xml
<?xml version="1.0" encoding="UTF-8"?>
<body xmlns="http://www.tei-c.org/ns/1.0" n="spleenEtIdeal">
    <div type="longPoem">
        <head>Les Phares</head>
        <lg type="stanza">
            <l n="1">Rubens, fleuve d'oubli, jardin de la paresse,</l>
            <l n="2">Oreiller de chair fraîche où l'on ne peut aimer,</l>
            <l n="3">Mais où la vie afflue et s'agite sans cesse,</l>
            <l n="4">Comme l'air dans le ciel et la mer dans la mer ;</l>
            <!-- nœud commentaire -->
        </lg>
        <lg type="stanza">
            <l n="5">Léonard de Vinci, miroir profond et sombre,</l>
            <l n="6">Où des anges charmants, avec un doux souris</l>
            <l n="7">Tout chargé de mystère, apparaissent à l'ombre</l>
            <l n="8">Des glaciers et des pins qui ferment leur pays ;</l>
        </lg>
        <gap reason="sampling" quantity="9" unit="stanza"/>
    </div>
    <div type="longPoem">
        <head>La Muse malade</head>
        <gap reason="sampling" quantity="4" unit="stanza"/>
    </div>
</body>

```

???

TEI is a common model for all the different publication projects engaged in SynopsX.

---

# TEI as 3 layer cake

![tei3layercake](images/structureTEI.svg)

---

template: inverse
class: center middle

# .red[2.] explore/visualize

---

# XQuery full-text

## build a personalized engine

## unique layer application

## articulation with web service

---

# lemmatisation

![dataviz](images/schiller.png)

???

Some of the specific historical datas we are dealing with need specific lemmanisation.

In that use case, the XQuery Full-text standard implementation in BaseX could be very usefull to built by ourselves this language treatments.

---

# lemmatisation

![datavis](images/dta--cab.png)


---

# dataviz

![datavis](images/datavis.png)

???

---

# dataviz

![datavis](images/EquivalencesView_Ordine_level2.jpg)

---

template: inverse
class: center middle

# .red[3.] enrich/link

---

# a linked corpus

 ![lod](images/sw-cube.png)

## take part of .red[L]inked .red[O]pen .red[D]ata
- for distribution and re-use
- for enrichment

---

# a linked corpus

![livre](images/hugo.png)
---

# content negociation

## HTTP header

## consumes / produces

## RESTXQ

---

# XQuery Update

![Annotator](images/annotator.png)

???

The rich fonctionalities of XQuery update are expected to be used to implement an annotating client as annotator.js to be able to annotate the sources directly in XML-TEI.

But XQuery Update could also use to manipulate collections of texts in the data base for bunk changes, etc.

---

# a candidate facility for the french research infrastructure TGIR Huma-Num

TGIR Huma-Num's infrastructure is composed of :

- 12 To for storage capacity for the Information Systems
- 120 To for general secured storage
- 100 computational cores
- 18 servers

???

- the TGIR Huma-Num http://www.huma-num.fr is a very large facility which aims to facilitate the digital turn in humanities and social sciences. TGIR Huma-Num coordinates the  participation of France in the European digital research infrastructure for the arts and humanities DARIAH http://www.dariah.fr

The scope of SynopsX is on the one hand to help a single researcher to easily publish, explore and expose their XML data, and on the other hand for ITs teams to collaborate, mutualize and genericize their efforts. The project is candidate to join the facilities offered to researchers in arts and humanities by the TGIR Huma-Num.

---

# why SynopsX ?

## .red[collaborate]
- research by projects
- code quality & best practices

## .red[mutualise]
- not reinventing the wheel
- sustainability

## .red[genericize]
- maintainability
- reusability


???

---

template: inverse
class: align center

# Questions ?

https://github.com/ahn-ens-lyon/synopsx
