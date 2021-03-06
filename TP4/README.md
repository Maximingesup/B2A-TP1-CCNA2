Menu 2 : Infra campus
=================

# Consignes

**Fournir un réseau stable à un grand nombre de clients sur un même site.**

#### > Locaux
* 3 bâtiments
  * 2 étages, 5 salles/étages
  * chaque salle supporte au mini 30 clients

#### > Clients du réseau

* ~200 étudiants
  * en moyenne, ils ont 1,5 équipements
    * tous ont un PC
    * certains utilisent smartphone/tablette avec la wifi
* ~50 profs
  * en moyenne, ils ont 1,5 équipements
    * tous ont un PC
    * certains utilisent smartphone/tablette avec la wifi
* ~20 serveurs
* 15 caméras
* 2 admins

#### > Besoin

* les étudiants ont accès à 10 serveurs sur les 20
* les profs ont accès à tous les serveurs
* les admins ont accès à tous les serveurs et aux caméras
* débit descendant WAN exigé : 
  * étudiant/profs/admins : 1Mo/sec
  * serveur : 5Mo/sec

#### > Rendu attendu

* plan d'adressage IP
* plan des VLANs
* schéma de la topologie
* matériel nécessaire
  * pas dans les détails, mais au moins la quantité
  * les câbles, ça compte
* maquette GNS3

> **HINT**  mettez en place une **archi 3-tier** (core/distribution/access) (on aura une partie théorique là-dessus)

---

# Topologie

![Schéma réseau](https://user-images.githubusercontent.com/34605772/56131983-2d7f8180-5f89-11e9-82c4-79ce780fba49.png)



3 Bâtiments avec rez de chaussée et 2 étages, 15 salles par bâtiment, 5 salles par étages
Nombre de salles à desservir : 45 salles


Matériel nécessaire pour la création de l’infrastructure: 
50 switchs
4 routeurs
57 câbles au total
6 vm (2 pour les serveurs, 1 pour admin, 1 pour prof,1 pour élève, 1 pour les caméras) 

Plan d'adressage


| Hosts    | lab4-net1         |
|----------|-------------------|
| Client1  | 10.0.0.1          |
| Admin    | 10.0.0.2          |
| Prof     | 10.0.0.3          |
| Elève    | 10.0.0.4          |
| Caméra   | 10.0.0.5          |
| Serveur1 | 10.0.0.6          |
| Serveur2 | 10.0.0.7          | 


| Hosts    | lab4-net1         | lab4-net2             | lab4-net3            | lab4-net4            | lab4-net5            |
|----------|-------------------|-----------------------|----------------------|----------------------|----------------------|
| Routeur1 |                   | 10.2.0.1/30  port 1/0 | 10.1.0.1/30 port 2/0 |                      |                      |
| Routeur2 | 10.0.0.8 port 0/0 |                       |                      | 10.3.0.2/30 port 3/0 | 10.4.0.2/30 port 2/0 |
| Routeur3 |                   | 10.2.0.2/30 port 1/0  |                      |                      | 10.4.0.1/30 port2/0  |
| Routeur4 |                   |                       | 10.1.0.2/30 port 2/0 | 10.3.0.1/30 port 3/0 |
