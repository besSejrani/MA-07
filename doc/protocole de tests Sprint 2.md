# Protocole de test Sprint 2

## Config Linux locale

### 1 - Debian 10 Buster version stable

Afficher la version
```
hostnamectl
```
Verifier la les mise a jour
```
sudo apt update
```
Executer les mise a jours
```
sudo apt update
```

### 2 - Les partitions

Montrer les partitions
```
lsblk
```

### 3 - Config de base

Afficher le processeur
```
lscpu
```
Afficher la RAM
```
free -m
```
Stresser le swap
```
stress-ng --vm 2 --vm -bytes 1G -timeout 60s &
```

### 4 - Config de l'OS

Afficher la langue
```
cat /etc/default/locale
```
Afficher la langue du clavier
```
cat /etc/default/keyboard
```
Afficher le nom d'hôte
```
hostname
```
Afficher le nom de domaine
```
hostname -d
```
Montrer utilisateur sudo
```
sudo apt update
```
Montrer utilisateur normal
```
sudo apt update
```

## Accès admin Linux

### 1 - Accès SSH

Utilliser

### 3 - Accès en root impossible via SSH

Montrer config ssh
```
sudo nano /etc/ssh/sshd_config
```
Essayer de faire la commande `su` et montrer que ça ne marche pas

Connection ssh au `root`
```
ssh root@gamper.ninja
```

## Pare-feu

Montrer connection externe
```
ping google.com
```

Afficher le fichier de config
```
nano /etc/nftables.conf
```

Validation

  Connection au rasberry
  ```
  ssh pi@192.168.1.5
  ```
  Executer un scan des port accesssible

  ```
  nmap -v -Pn 192.168.1.34
  ```

