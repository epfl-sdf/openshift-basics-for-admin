%Openshift pour administrateurs systèmes
%Marc Schär
%1er septembre 2015

# Introduction

### Openshift Origin

\setbeamertemplate{caption}{\raggedright\insertcaption\par}
\begin{figure}[htp]
  \center
  \includegraphics[width=5cm]{img/openshift-origin-logo.png}
  \caption{Openshift Origin - The Opensource version of Openshift}
\end{figure}


### Qu'est-ce qu'Openshift ?

* Solution PaaS (Platform as a Service)

. . .

* Création rapide d'un environnement de développement

. . .

* Haute disponibilité (HA Proxy) pour les applications

. . .

* Accès aux machines contenant les applications via SSH

. . .

* Gestion du code des applications par git


### Que peut-on faire avec ?

Un utilisateur peut :

* Installer des applications (Wordpress par ex.)

. . .

* Créer ses applications (Ruby, Python, PHP,...)

. . .

* Créer ses propres cartridges
    * Ajoute une fonctionnalité à une application
        * Ruby, Jenkins, PHP,...

. . .

* Accéder à ses machines via SSH

. . .

* Gérer ses applications via git


# Architecture

### Les rôles dans Openshift

* Node - MCollective Agent
    * Contient les applications des utilisateurs

. . . 

* Broker - MCollective Client
    * Fournit une API REST à l'utilisateur
    * Gère les noeuds

. . .

* Nameserver - BIND
    * Serveur de noms pour Openshift
        * Pour les hôtes d'Openshift
        * Pour les applications

. . . 

* Datastore - MongoDB
    * Base de Données

. . .

* MsgServer - ActiveMQ
    * Serveur de messagerie
    * Relie les brokers et les noeuds

### Interconnectivité

\setbeamertemplate{caption}{\raggedright\insertcaption\par}
\begin{figure}[htp]
  \center
  \includegraphics[width=8cm]{img/diagramme_relations_oo.png}
  \caption{Connaissances entre les éléments d'Openshift}
\end{figure}

### Architecture - Résumé

\setbeamertemplate{caption}{\raggedright\insertcaption\par}
\begin{figure}[htp]
  \center
  \includegraphics[width=9cm]{img/resume.jpg}
  \caption{Source: Openshift Enterprise par Ali Sadeghi Ardestani}
\end{figure}

# Organisation des applications

### Qui est concerné ?

Les concernés sont :

. . .

* Broker
    * Organise les regroupements de noeuds
    * Place les applications dans les noeuds

. . .

* Nodes
    * Contient les applications (gears)


## Organisation des Noeuds

### Profile

Un noeud est défini par un profile qui contient :

* Un nom (small, medium, large,...)

. . .

* Un quota de fichiers par application

. . .

* Un nombre maximum d'applications sur le noeud

. . . 

* Le nombre maximum de processeurs par applications

. . . 

* La limite de mémoire

. . .

* Et bien d'autres options...


### District

Le district sert à regrouper des noeuds :

* De même profile uniquement...

. . . 

* Mais pas forcément tous les noeuds du même profile !

. . .

Pourquoi un district ?

. . . 

* Choix du noeud dans le district pour une application

. . .

* Réplication d'applications dans des noeuds du même district (HA Proxy)


### Possibilité d'utilisation

\setbeamertemplate{caption}{\raggedright\insertcaption\par}
\begin{figure}[htp]
  \center
  \includegraphics[width=8cm]{img/openshift-enterprise-24-638.jpg}
  \caption{Source: Openshift Enterprise par Ali Sadeghi Ardestani}
\end{figure}

### Quelques commandes pour gérer les noeuds

* Lister les noeuds libres
```sh
# oo-admin-ctl-district -c list-available
```

. . .

* Créer un district
```sh
# oo-admin-ctl-district -c create -n <district_name> \ 
-p <profile>
```

. . . 

* Lister les districts
```sh
# oo-admin-ctl-district
```

. . . 

* Ajouter un noeud à un district
```sh
# oo-admin-ctl-district -c add-node -n <district_name> \
-i <node_name>
```

. . . 

* Activer les cartridges
```sh
# oo-admin-ctl-cartridge -c import-node \
-n <district_name> --activate
```

# Installation via Puppet

### Module Openshift Origin

* Installation d'Openshift automatisée
    * Spécification des rôles pour une machine

. . . 

* Possibilité de HA
    * Broker
    * Datastore
    * MsgServer

. . .

* Utilisation de Consul pour la reconnaissance entre noeuds d'une même instance

# Conclusion

### Conclusion

* Machines accessibles simplement et rapidement pour l'utilisateur

. . .

* Gestion des noeuds relativement simple

. . .

* Scalable facilement

. . .

* Permet le déploiement d'environnement de développement et de production facilement

### Aller plus loin

* Openshift : [https://www.openshift.com/][openshift]

. . .

* Test en local : 
[https://github.com/AblionGE/puppet-openshift-origin-example][exemple]

. . .

* Slides d'Openshift Enterprise par Ali Sadeghi Ardestani : [http://www.slideshare.net/AliSadeghiArdestani/pn-t3-openshift][OE]

. . .

* Documentation d'Openshift Origin M4 : [https://docs.openshift.org/origin-m4/index.html][doc]

. . .

* Pour jouer : [https://openshift-demo.si.epfl.ch][openshift-demo]


[openshift]: https://www.openshift.com/
[exemple]: https://github.com/AblionGE/puppet-openshift-origin-example
[OE]: http://www.slideshare.net/AliSadeghiArdestani/pn-t3-openshift
[doc]: https://docs.openshift.org/origin-m4/index.html
[openshift-demo]: https://openshift-demo.si.epfl.ch


### La nouvelle version

Openshift Origin 3 sorti en juin 2015 contient :

* Création d'applications dans un Docker[^1]

. . .

* Utilisation de Kubernetes comme orchestrateur de containers[^2]

. . .

* Projet Atomic comme système d'exploitation[^3]


[^1]: [https://www.docker.com/whatisdocker][docker]
[^2]: [http://kubernetes.io/][kubernetes]
[^3]: [http://www.projectatomic.io/docs/][atomic]

[docker]: https://www.docker.com/whatisdocker
[kubernetes]: http://kubernetes.io/
[atomic]: http://www.projectatomic.io/docs/
