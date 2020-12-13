# Utilisateurs

## Administration Utilisateurs

### Création  d'un utilisateur

```text
adduser mysql
```

### Suppression d'un utilisateur

```text
deluser mysql
```

### Renommer un utilisateur

Pour pouvoir renommer un utilisateur, il faut au préalable que la session du compte sois fermée.

```text
usermod -l nouveauNom ancienNom
```

### Définir le mot de passe utilisateur

```text
passwd motDePasse
```

### Ajouter un utilisateur existant à un groupe

```text
sudo usermod -aG groupe utilisateur
```

### Ajouter un nouvel utilisateur à un groupe

```text
useradd -G groupe utilisateur
```

### Supprimer un utilisateur d'un groupe

```text
gpasswd -d utilisateur groupe
```

### Lister tous les utilisateurs

```text
getent passwd

cat /etc/passwd
```

## Administration Groupes

### **Créer un groupe**

```text
groupadd groupe
```

### Supprimer un groupe

```text
groupedel groupe
```

### **Renommer un groupe**

```text
groupmod -n nouveauNom ancienNom
```

### **Lister les groupes d'un utilisateur**

```text
groups

id utilisateur
```

### **Lister tous les groupes**

```text
getent group

cat /etc/group
```

## Sources

|  |  |
| :--- | :--- |
|  |  |

