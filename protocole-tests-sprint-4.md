# Protocole Tests Sprint 4

## Théorie

### Scripting sous Linux

| Permission Unique | Symbole | Niveau |
| :--- | :---: | :---: |
| Permission lecture | r | 4 |
| Permission écriture | w | 2 |
| Permission d'exécution | x | 1 |
| Pas de permission | - | 0 |

| Permissions combinées | Symbole | Niveau |
| :--- | :---: | :---: |
| L' utilisateur peut lire, écrire et exécuter | rwx | 7 |
| L'utilisateur peut uniquement lire et écrire | rw- | 6 |
| L' utilisateur peut uniquement lire et exécuter | r-x | 5 |

| Permissions multiples | Symbole | Niveau |
| :--- | :---: | :---: |
| Le propriétaire et le groupe ont tous les droits | rwxrwx--- | 770 |
| Toutes les permissions pour tout le monde | rwxrwxrwx | 777 |
| Uniquement le propriétaire à toute les permissions | rwx------ | 700 |

### Scripting sous Linux

```text
#!/bin/bash

function listArguments(){
    for i in $@; do
        echo $i
    done;
}

listArguments $@

./listArguments.sh hello world cpnv
```

### Compression de fichier sous Linux

```text
#Create file
touch bla.txt

#Create tarball from bla.txt
tar -cvf new.tar bla.txt

#Show size
du -sh new.tar

#Compress tarball
gzip -v new.tar

#Uncompress tarball
gunzip -v new.tar.gz

#Extract tarball
tar -xvf new.tar

#Extract tarball to specific location
tar -C ~/Desktop -xvf new.tar
```

## Partage Réseau

### smb expose une zone publique offre des dossiers et fichiers en lecture seule

```text
# Create a folder
sudo mkdir /home/Public


# Add public permission to the folder
sudo chmod 0744 /home/Public
sudo chown -R nobody:nogroup /home/Public


#Modify samba configuration file
sudo nano /etc/samba/smb.conf

# Add content
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = ubuntu
security = user
map to guest = bad user
name resolve order = bcast host
dns proxy = no
bind interfaces only = yes

# Public access configuration
[Public]
   path = /home/Public
   writable = yes
   guest ok = yes
   guest only = yes
   read only = no
   create mode = 0777
   directory mode = 0777
   force user = nobody

      
# Restart Samba
sudo systemctl restart smbd
```

### smb expose une zone privée par utilisateurs qui offre des droits privilégiés

```text
# Create a folder
sudo mkdir /home/Private


#Create a group
sudo groupadd security


#Grant permissions to the group
sudo chgrp security /home/Private
sudo chmod -R 0770 /home/Private


#Modify samba configuration file
sudo nano /etc/samba/smb.conf

#Add content
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = ubuntu
security = user
map to guest = bad user
name resolve order = bcast host
dns proxy = no
bind interfaces only = yes

# add to the end
[Private]
   path = /home/Private
   writable = yes
   guest ok = no
   read only = no
   browsable = yes
   create mode = 0777
   directory mode = 0777
   valid users = @security

      
#Add members to group
sudo usermod -aG security richard


#Create user password
sudo smbpasswd -a richard


#Restart Samba
sudo systemctl restart smbd
```

## Moteur de base de données

### Bonnes pratiques respectées

### Accès depuis le serveur de base de données \(en local\)

### Accès uniquement pour un client \(voir schéma\)

## Environnement

### Comment accéder au sous réseau privé

```text
ssh -L port:host:port user@host
```

![https://docs.bitnami.com/virtual-machine/faq/get-started/access-ssh-tunnel/ ](.gitbook/assets/12.png)

![https://docs.bitnami.com/virtual-machine/faq/get-started/access-ssh-tunnel/](.gitbook/assets/13.png)

### Identifier les ports et les protocoles à autoriser \(ainsi que le sens de communication\)

| Service | Port | Protocole |
| :--- | :--- | :--- |
| MySQL | 3306 | TCP |
| SMB | 445 | SMB |

### Identifier les rôles de chaque instance

## Sources

| Titre | Lien |
| :--- | :--- |
| Create a Public Samba Share on Ubuntu | [Lien](https://websiteforstudents.com/create-public-samba-share-ubuntu-17-04-17-10/) |
| Create a Private Samba Share on Ubuntu | [Lien](https://websiteforstudents.com/create-private-samba-share-ubuntu-17-04-17-10/) |

