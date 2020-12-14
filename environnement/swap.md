# Linux Swap

## **Description**

Le Swap est un espace sur un disque qui est utilisé lorsque la quantité de mémoire RAM physique est pleine. Lorsqu'un système Linux manque de RAM, les pages inactives sont déplacées de la RAM vers l'espace de swap.

Cet espace peut prendre la forme d'une partition de SWAP dédiée ou d'un fichier d'échange.

## **Attention**

L'utilisation de l'espace d'échange ralentit significativement le système et entraîne une activité permanente du disque dur, provoquant une usure prématurée du matériel. De ce fait, l'espace d'échange ne doit pas être considéré comme un remplacement de votre mémoire vive physique, mais plutôt comme un mécanisme d'appoint.

Dans la plupart des cas, lors de l'exécution de Linux sur une machine virtuelle, une partition de swap n'est pas présente, donc la seule option est de créer un fichier de swap.

## **Recommandations**

Il n'y a pas qu'une seule règle définissant la quantité d'espace à allouer à la zone d'échange. Cependant, on peut relever [des recommandations généralement acceptées](https://doc.ubuntu-fr.org/tutoriel/partitionner_manuellement_avec_installateur_ubuntu#partitions_indispensables) :

L’ ordinateur dispose de 6 Go de RAM ou plus.  
Allouez un espace d'échange égal à la taille de votre RAM ;

L’ ordinateur dispose de 1 Go de RAM à 4Go  
Allouez un espace d'échange de 1× à 1,5× la taille de votre RAM ;

L’ ordinateur dispose de moins de 1 Go de RAM  
Allouez un espace d'échange de 1,5× à 2× la taille de votre RAM.

## **Partition**

### **Ajout Partition**

```text
swapon
```

### **Ajout Fichier**

Création d'un fichier swap

```text
sudo fallocate -l 1G /swapfile
```

### **Permissions**

```text
sudo chmod 600 /swapfile
```

### **Formater**

```text
sudo mkswap /swapfile
```

### **Enable swap**

```text
sudo swapon /swapfile
```

If you want the changes to be permanent, you need to edit the /etc/fstab file and add the following.

```text
/swapfile swap swap defaults 0 0
```

### **Status swap**

```text
sudo free -h
```

### **Suppression Fichier**

```text
sudo swapoff -v /swapfile

sudo rm /swapfile
```

### **Ajustement valeur**

```text
cat /proc/sys/vm/swappiness
```

Devault Value

```text
sudo nano /etc/sysctl.conf
```

Recommanded value

```text
vm.swappiness=10
```

## **Architecture**

Debian Duster est construit en architecture amd64.

