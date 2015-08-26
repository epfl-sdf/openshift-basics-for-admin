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

* Broker
* Nameserver
* Datastore
* MsgServer
* Node

### Broker

mcollective

### Nameserver

bind

### Datastore

Mongodb

### MsgServer

activemq

### Node

gear

### Interconnectivité

SCHEMA


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

### District

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
