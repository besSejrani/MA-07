# Protocole Tests Sprint 4

## Théorie

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
touch bla.txt
tar -cvf new.tar bla.txt

#Show size
du -sh new.tar

#Compress tar file
gzip -v new.tar

#Uncompress tar file
gunzip -v new.tar.gz

#Extracting tar file
tar -xvf new.tar

#Extracting tar file to specific location
tar -C ~/Desktop -xvf new.tar
```

## Partage Réseau

## Moteur de base de données

## Environnement

## Sources

| Titre | Lien |
| :--- | :--- |
| Create a Public Samba Share on Ubuntu | [Lien](https://websiteforstudents.com/create-public-samba-share-ubuntu-17-04-17-10/) |

