# Utilisateurs

## Administration Utilisateurs

### Création  d'un utilisateur

```text
adduser utilisateur
```

### Suppression d'un utilisateur

```text
deluser utilisateur
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

### Ajouter un utiisateur au groupe administrateur

```text
useradd -G sudo utilisateur
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

## Sources

|  |  |
| :--- | :--- |
|  |  |

