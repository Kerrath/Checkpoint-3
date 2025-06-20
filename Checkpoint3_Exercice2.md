# Partie 1 : Gestion des utilisateurs

- Q.2.1.1 Sur le serveur, créer un compte pour ton usage personnel.
![Q2.1.1.png](https://i.ibb.co/1GXDVb9r/Q2-1-1.png)
- Q.2.1.2 Quelles préconisations proposes-tu concernant ce compte ?
	- Utiliser un mot de passe fort
	- Ajouter le compte au groupe Sudo


# Partie 2 : Configuration de SSH

- Q.2.2.1 Désactiver complètement l'accès à distance de l'utilisateur root.
![Q2.2.1.png](https://i.ibb.co/FLCSLPzK/Q2-2-1.png)
- Q.2.2.2 Autoriser l'accès à distance à ton compte personnel uniquement.
![Q2.2.2.png](https://i.ibb.co/fYJCqG59/Q2-2-2.png)
- Q.2.2.3 Mettre en place une authentification par clé valide et désactiver l'authentification par mot de passe
![Q2.2.3.png](https://i.ibb.co/zT8yHLrK/Q2-2-3.png)

# Partie 3 : Analyse du stockage

- Q.2.3.1 Quels sont les systèmes de fichiers actuellement montés ?
	- ext4 et ext2
- Q.2.3.2 Quel type de système de stockage ils utilisent ?

- Q.2.3.3 Ajouter un nouveau disque de 8,00 Gio au serveur et réparer le volume RAID

- Q.2.3.4 Ajouter un nouveau volume logique LVM de 2 Gio qui servira à héberger des sauvegardes. Ce volume doit être monté automatiquement à chaque démarrage dans l'emplacement par défaut : /var/lib/bareos/storage.

- Q.2.3.5 Combien d'espace disponible reste-t-il dans le groupe de volume ?

# Partie 4 : Sauvegardes

- Q.2.4.1 Expliquer succinctement les rôles respectifs des 3 composants bareos installés sur la VM.
	- Bareos Director : il gère la planification, le contrôle et le lancement des tâche de sauvgardes
	- Bareos Console : Permet a l'utilisateur de communiquer avec Bareos Director
	- Catalog : BDD où est enregistrer toutes les tâches de sauvegardes, leurs résultats, les fichiers sauvegardés, etc.

# Partie 5 : Filtrage et analyse réseau

- Q.2.5.1 Quelles sont actuellement les règles appliquées sur Netfilter ?

- Q.2.5.2 Quels types de communications sont autorisées ?
	- le icmp pour ip
	- tcp pour ssh
	- icmpv6 pour ip6
- Q.2.5.3 Quels types sont interdit ?
	- tous les autre protocol
- Q.2.5.4 Sur nftables, ajouter les règles nécessaires pour autoriser bareos à communiquer avec les clients bareos potentiellement présents sur l'ensemble des machines du réseau local sur lequel se trouve le serveur.

# Partie 6 : Analyse de logs

- Q.2.6.1 Lister les 10 derniers échecs de connexion ayant eu lieu sur le serveur en indiquant pour chacun :  La date et l'heure de la tentative.
```
- Dec 20 10:24:08 cp3 sshd[499]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.0.0.199  user=root
- Dec 21 14:12:30 SRVLX01 login[496]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser= rhost= 
- Dec 21 14:39:27 SRVLX01 su: pam_unix(su-l:auth): authentication failure; logname=wilder uid=1000 euid=0 tty=pts/0 ruser=wilder rhost=  user=root
- Jan  3 11:06:28 cp3 sshd[1157]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.0.0.199  user=root
- Jan  3 11:06:43 cp3 sshd[1161]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.0.0.199  user=wilder
- Jan  3 11:23:00 cp3 sshd[1227]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.0.0.199 
- Jan  3 11:23:31 cp3 sshd[1231]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.0.0.199  user=root
- Jan  3 11:23:45 cp3 sshd[1231]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.0.0.199  user=root
- Jan  3 12:09:26 cp3 sshd[1587]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=fd26:ba41:c8d6:0:ba92:6393:cc55:8b8d 
- Jan  3 12:09:37 cp3 sshd[1587]: PAM 1 more authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=fd26:ba41:c8d6:0:ba92:6393:cc55:8b8d 
```