%Openshift pour administrateurs systèmes
%Marc Schär
%1er septembre 2015

# Introduction

### Openshift

LOGO

### Qu'est-ce qu'Openshift ?

* Solution PaaS (Platform as a Service)

. . .

* Création rapide d'un environnement de développement

. . .

* Haute disponibilité (HA Proxy) pour les applications

. . .

* ...

### Que peut-on faire avec ?

cartridges, applications, git, ssh


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

Liens
