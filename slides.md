%Openshift pour administrateurs systèmes
%Marc Schär
%1er septembre 2015

# Introduction

### Openshift Origin

\setbeamertemplate{caption}{\raggedright\insertcaption\par}
\begin{figure}[htp]
  \center
  \includegraphics[width=8cm]{img/openshift-origin-logo.png}
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

* Node
    * Contient les applications des utilisateurs

. . . 

* Broker - MCollective
    * Fourni une API REST à l'utilisateur
    * Gère les noeuds

. . .

* Nameserver - Bind
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

# Organisation des applications

### Qui est concerné ?

Les concernés sont :

. . .

* Broker
    * Organise les regroupements de noeuds

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




### SCHEMA organisation

### Démonstration

Ligne de commande


# Haute disponibilité

### Broker (HA Proxy)

maitre - esclave

### Datastore (Redondance)

### MsgServer (Redondance)


# Installation via Puppet

### Module Openshift Origin

* Installation d'Openshift automatisée
    * Spécification des rôles

. . . 

* Possibilité de HA
    * Broker
    * Datastore
    * MsgServer

# Conclusion

### Conclusion

### Aller plus loin

Test en local : github d'exemple

### La nouvelle version

Openshift Origin 3 contient :

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
