---
documentclass: article
graphics: true
title: Developpement d'une application pour système d'alarme sur tablette
subtitle: Rapport de stage de 1ère année efféctué du 12 Juin au 1 Septembre 2023
titlegraphic: images/cytech
institute: CY Tech X Ae&t
date: 12/06/2023 - 01/09/2023
author: 

- Nicolas DURAND
toc: true
toc-title: Table des matières
header-includes: |
  \usepackage{caption}
  \usepackage{subcaption}
  \usepackage{ dsfont }
  \usepackage{ amssymb }
  \usepackage{ tipa }
  \usepackage{ stmaryrd }


geometry: margin=2.5cm
fontsize: 12pt
fontfamily: fourier
linestretch: 1.5
indent: true
papersize: a4

---

# 0. Remerciements

\clearpage
# 1. Introduction

&nbsp;&nbsp;&nbsp;&nbsp;Dans le cadre de la 1ère année de mon cycle Ingénieure en Génie Informatique à **Cy-Tech**, j'ai réalisé un stage de 10 semaines (du 12 Juin au 1 Septembre 2023) au sein du **BE** (bureau d'étude) d' **Ae&t** (Application Electronique Techniques) à Jurançon. J'ai eu vent de cette opportunité via le **career center de Cy-Tech** et ai choisi de faire une demande de stage à ae&t pour de nombreuses raisons. J'avais d'abord l'envie de découvrir le monde professionel dans le **développement logiciel**. Ensuite, cette expérience était l'occasion d'utiliser toutes les connaissances et compétences que j'ai pu apprendre depuis ces dernières années afin de réaliser un objectif concret. Enfin, la possibilité de travailler pour une entreprise local et historique de Pau et sa périphérie m'a d'autant plus motivé.    
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;Je vais tout d'abord vous présenter dans ce rapport l'entreprise qui m'a accueilli et l'équipe avec qui j'ai réalisé mon stage. Suite à quoi je développerai la mission qui m'a été confié et son déroulement ainsi que les technologies utilisé et conclurai par un bilan de ces 8 semaines de stage à l'heure de ce rapport. En effet, il reste encore 2 semaines de stage afin de finaliser le projet, la date de rendu de ce rapport étant le 15 Août.  
&nbsp;  

&nbsp;&nbsp;&nbsp;&nbsp;Le but initial de ce stage était la confection **UI/UX** (Interface Utilisateur / eXperience Utilisateur) d'une **IHM** (Interface Homme Machine) reconfigurable à l'aide d'un fichier de configuration au format JSON, il évolura par la suite intégrant le développement plus poussé du backend (partie machine / serveur) de l'application avec la gestion des systemes d'alarmes sur le réseau.   

\clearpage

# 2. Ae&t : l'entreprise d'accueil 

## &nbsp;&nbsp;2.1. Qui sont-ils ?

&nbsp;&nbsp;&nbsp;&nbsp;Fondé en 1976 par Robert Joseph, ae&t était a la base une petite entreprise qui vendait des lampes flash dans son garage. Après être parti à la retraite 10 ans plus tard en 1986, son fils, Jean-Yves Joseph, reprit la boite familial et développa en plus des lumières, des systemes d'alarmes dont certains sont conforme à la réglementation ATEX (utilisable en zone explosive). Vous l'aurez compris l'objectif principal d'Ae&t est de signaler et protéger autant les lieux publics comme les écoles et gares que les usines à haut risque !

>**Slogan de Ae&t :** <br>&nbsp;&nbsp;&nbsp;&nbsp;entre nous, protéger la vie 

&nbsp;&nbsp;&nbsp;&nbsp;L'entreprise est comporte 2 corps principaux : la partie commercial responsable des ventes et de la promotion de ae&t et le bureau d'étude, partie dans laquelle j'ai effectué mon stage, qui est responsable de la conception de nouveaux produits. Cette part est moteur de l'innovation de ae&t et c'est notamment grace à ces innovations que l'entreprise c'est vu décerner de nombreux *trophées de l'innovation* tel que pour le ... en 199 ou encore le ... en 199.

&nbsp;&nbsp;&nbsp;&nbsp;Cependant il ne sont pas les seules dans ce milieu, de nombreux gros concurrents mondiaux connue au niveau des systèmes de télécommunications d'alerte tel que *Telegraphia* une société Tchécoslovaque, *Ateis* entreprises Française spécialisée dans le public address ou encore *Commend* d'origine Autrichienne.

&nbsp;&nbsp;&nbsp;&nbsp;Le ODD


## &nbsp;&nbsp;2.2. Hauts fait

&nbsp;&nbsp;&nbsp;&nbsp;Suite à son expension dans les locaux actuels à Jurançon en 1990, ae&t à reçu de nombreux prix et trophées tel que le trophées des "***AS de l'entreprise en Béarn et Soule***" à 3 reprises! 

&nbsp;&nbsp;&nbsp;&nbsp;Ae&t à de nombreux très grands succès à son actif, en effet suite à son expension dans les locaux actuels à Jurançon en 1990, ae&t à reçu de nombreux prix et trophées tel que le trophées des "***AS de l'entreprise en Béarn et Soule***" à 3 reprises! Ils ont aussi décroché de gros contracts tels que la commandes d'alarmes sonores et optiques dans 16 centrales nucléaires EDF, d'alarmes d'évacuation indendie pour le palais des festivals de cannes ou encore la signalisation lumineuse durant les travaux du tunnel sous la Manche et sont responsable, encore à ce jour, du système d'illumination de le Tour Eiffel !

(image tour effiel illuminé)


# 3. Le déroulement du stage

## &nbsp;3.1. La mission

### &nbsp;&nbsp;3.1.1. Le contexte

&nbsp;&nbsp;&nbsp;&nbsp; Un des élements très aimé par les clients d'ae&t est l'AP8, un pupitre de commande des systèmes d'alarmes VIGInet. Totalement configurable, il peut activer/désactiver les alarmes, communiquer des messages vocaux et affiche les différentes erreurs sur les boities d'alarmes! Cependant il souffre de quelques défaut : chaque pièce demande une longue personnalisation éléctronnique et la remonté d'information est très difficile à comprendre, en effet il ne peut transmettre des informations que par quelques LED comme on peut le voir [ci-dessous](AP8).

&nbsp;&nbsp;&nbsp;&nbsp; On en arrive à la raison du stage. L'objectif était le portage de l'AP8 vers une application tablette.Il nous été initialement demandé de développé une interface intelligente configurable via un fichier de configuration général au format json, le stage fut assez vite étendu au développement de plus complet de l'application avec la communication entre l'application et les boitiers d'alarmes.

(image AP8)
\clearpage
### &nbsp;&nbsp;3.1.2. Les outils et technologies du projet

Tous les outils et technologies utilisés dans le cadre du projet sont **open source**.

#### &nbsp;&nbsp;&nbsp;Linux Mint

&nbsp;&nbsp;&nbsp;&nbsp; **Linux Mint** est une distribution Linux dérivé de **Ubuntu** et **Debian** dont le développement commençât en 2006. Elle en est aujourd'hui à sa version 21.2 (nom de code **Victoria** ) et c'est aussi la version utilisé lors du stage.  

#### &nbsp;&nbsp;&nbsp;Méthode AGILE : Scrum

&nbsp;&nbsp;&nbsp;&nbsp; Les **méthodes AGILES** sont des pratiques de collaboration entre équipes auto-oragnisées. Scrum est un groupe de pratiques répondant pour la plupart aux préconisation du manifeste agile. Il s'appuie sur le découpage d'un projet en sprints séparer (planification -> programmation -> présentation)

#### &nbsp;&nbsp;&nbsp;Figma

&nbsp;&nbsp;&nbsp;&nbsp; **Figma** est un outil web de prototypage basé sur la conception d'**UI/UX** (interfact utilisateur et expérieence utilisateur) en mettant l'accent sur la collaboration en temps réel.

#### &nbsp;&nbsp;&nbsp;VueJs

&nbsp;&nbsp;&nbsp;&nbsp; **VueJs** est un framework javascript designer pour pour la création d'interface utilisateur et d'application web. Il se base sur de la programmation par composent qui seront monté sur la page en temps réel

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ElectronJS

&nbsp;&nbsp;&nbsp;&nbsp; **Electron** est framework javascript basé sur **NodeJs** et maintenue par OpenJS rendant le développement d'application bureau plus simple, Electron est basé sur la technologie web et utilise une version de chromium pour l'affichage de l'interface.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Mqtt

&nbsp;&nbsp;&nbsp;&nbsp; **Mqtt** est un protocol de message basé sur le protocole **TCP/IPC** conçu pour ls connexions avec des sites distants où la bande passante réseau est limité. 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SSH

&nbsp;&nbsp;&nbsp;&nbsp; **SSH** ou Secure Shell est à la fois un programme informatique et un protocole de communication sécurisé. Son protocole de connexion impose un chiffrement bi-parti ou le client et le serveur possède une clé de chiffrement, il devient donc impossible de sniffer les informations.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RTP

&nbsp;&nbsp;&nbsp;&nbsp; **RTP** ou Real-time Transport Protocol est un protocole de communication informatique permettant le transfert de flux audio et video en temps réel. Il domine largement dans les domaine des communication comme la téléphonie, les applications de visioconférence ou encore les fonctionnalités push-to-talk basées sur le web

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Typescript et design pattern

&nbsp;&nbsp;&nbsp;&nbsp; **Typescript**

\clearpage
## &nbsp;&nbsp;3.2. Prototypage de l'IHM

&nbsp;&nbsp;&nbsp; La 


\clearpage
# Chapitre 3 :

# Conclusion

# Annexe

Ce stage m'a permis d'apprendre et de manipuler des technologies et méthodes de travail comme : 
 
 - Vue3js            : framework Javascript
 - Electronjs        : framework open-source développement logiciel
 - mqtt              : protocole de messagerie TCP/IP
 - ssh               : protocole de communication sécurisé TCP chiffré
 - RTP               : protocole de transmission audio (et video)
 - Typescript        : Javascript typé et plus sécurisé
 - design patterns   : template & methode de programmation réutilisable
 - SCRUM             : méthodes AGILE, travail en équipe 
 - figma             : outil de prototypage