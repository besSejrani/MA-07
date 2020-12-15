# Protocole Tests

## Config Linux locale

### 1 - Debian 10 Buster version stable

Afficher la version

```text
hostnamectl
```

Verifier la les mise a jour

```text
sudo apt update
```

Executer les mise a jours

```text
sudo apt update
```

### 2 - Les partitions

Montrer les partitions

```text
lsblk
```

### 3 - Config de base

Afficher le processeur

```text
lscpu
```

Afficher la RAM

```text
free -m
```

Stresser le swap

```text
stress-ng --vm 2 --vm -bytes 1G -timeout 60s &
```

### 4 - Config de l'OS

Afficher la langue

```text
cat /etc/default/locale
```

Afficher la langue du clavier

```text
cat /etc/default/keyboard
```

Afficher le nom d'hôte

```text
hostname
```

Afficher le nom de domaine

```text
hostname -d
```

Montrer utilisateur sudo

```text
sudo apt update
```

Montrer utilisateur normal

```text
sudo apt update
```

## SSH

### Accès en SSH

```text
ssh utilisateur@ip
```

### Accès en root impossible via SSH

```text
cat /etc/ssh/sshd_config
nano /etc/ssh/sshd_config
```

```text
PermitRootLogin: no
```

### Compte admin vs root

Le compte admin est limité aux autorisations qu'on lui donne, alors que root est Dieu, il peut tout faire

### Dessin de l'architecture client/server

![](../.gitbook/assets/download-1-.jpeg)

### Ajouter un utilisateur au groupe sudo

```text
sudo adduser foo sudo
```

## Pare-feu

Montrer connection externe

```text
ping google.com
```

Afficher le fichier de config

```text
nano /etc/nftables.conf
```

Validation

Connection au rasberry

```text
ssh pi@192.168.1.5
```

Executer un scan des port accesssible

```text
nmap -v -Pn 192.168.1.34
```

## Sources

| Titre | Lien |
| :--- | :--- |
| Sudo | [https://wiki.debian.org/sudo](https://wiki.debian.org/sudo) |
| Diagramme | [Image Hostinger](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.hostinger.com%2Ftutorials%2Fwp-content%2Fuploads%2Fsites%2F2%2F2017%2F07%2Fssh-client-and-server.jpg&f=1&nofb=1) |

