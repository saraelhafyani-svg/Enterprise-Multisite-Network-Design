
Auteur:

Encadrant : Prof. Azeddine KHIAT

Étudiante : Sara El Hafyani


Projet Final – Infrastructure Réseau Multisites Segmentée
Module

Réseaux Informatiques
(VLAN – EtherChannel – Router-on-a-Stick – Routage Statique WAN)

Objectif du Projet

Ce projet consiste à concevoir et déployer une infrastructure réseau d’entreprise multisite simulée avec Cisco Packet Tracer.
L’architecture mise en place vise à assurer :

Segmentation logique via les VLANs

Haute disponibilité grâce à EtherChannel (LACP)

Routage inter-VLAN avec Router-on-a-Stick

Interconnexion WAN entre plusieurs sites par routage statique

Validation complète par des tests réseau (ping, traceroute, tables de routage)

Topologie du Projet

Le réseau est composé de :

1 site principal (Siège)

2 sites distants interconnectés via des liaisons WAN série

3 routeurs (R1, R2, R3)

2 switches de niveau 2 (S1, S2)

Plusieurs VLANs utilisateurs et de gestion

(Les schémas et la topologie Packet Tracer sont disponibles dans ce dépôt)

🗂️ Plan d’Adressage
-VLANs (Siège)
VLAN	Usage	Réseau	Masque	Passerelle
10	Utilisateurs 1	172.18.10.0	/28	172.18.10.14
20	Utilisateurs 2	172.18.20.0	/28	172.18.20.14
30	Utilisateurs 3	172.18.30.0	/28	172.18.30.14
50	VLAN natif	172.18.50.0	/28	172.18.50.14
60	Admin / Gestion	172.18.60.0	/28	172.18.60.14
-WAN – Liaisons Série
Liaison	Réseau	IP Routeur
R1 – R2	10.0.30.176/30	R1: .177 / R2: .178
R1 – R3	10.0.30.180/30	R1: .181 / R3: .182
R2 – R3	10.0.30.184/30	R2: .185 / R3: .186
⚙️ Configuration Réseau
-Switching (Layer 2)

Création des VLANs : 10, 20, 30, 50, 60

Affectation des ports aux VLANs correspondants

Mise en place de EtherChannel (LACP) entre S1 et S2

Configuration du trunk sur Port-channel1

VLAN natif : 50

VLANs autorisés : 10, 20, 30, 50, 60

-Routage Inter-VLAN (Router-on-a-Stick – R1)

Activation de l’interface physique Fa0/0

Création des sous-interfaces par VLAN

Attribution des passerelles par défaut pour chaque VLAN

-Routage Statique WAN

Routes statiques configurées sur R1 vers les sites distants

Route par défaut configurée sur R2 et R3 vers R1

Phase de Validation

Les tests suivants ont été réalisés et documentés avec captures :

✔️ Ping inter-VLAN (VLAN 10 ↔ VLAN 20)

✔️ Traceroute vers un site distant (via R1 puis R3)

✔️ Ping de gestion (R1 → Switch S2)

✔️ Vérification des tables de routage (show ip route)
