**TP 3 Utilisateurs, groupes et permissions**

**Exercice 1**

1. 
```console
User@localhost:~$ groupadd dev
User@localhost:~$ groupadd infra
```
2. 
```console
User@localhost:~$ sudo useradd -m alice
User@localhost:~$ sudo useradd -m bob
User@localhost:~$ sudo useradd -m charlie
User@localhost:~$ sudo useradd -m dave
```
3.
```console
User@localhost:~$ sudo gpasswd -a alice dev
User@localhost:~$ sudo gpasswd -a bob dev
User@localhost:~$ sudo gpasswd -a dave dev
User@localhost:~$ sudo gpasswd -a bob infra
User@localhost:~$ sudo gpasswd -a charlie infra
User@localhost:~$ sudo gpasswd -a dave infra
```
4.
```console
User@localhost:~$ getent group
infra:x:1003:bob,charlie,dave

User@localhost:~$ grep infra /etc/group
infra:x:1003:bob,charlie,dave
```
5.
```console
User@localhost:~$ sudo usermod -m -d dev alice
User@localhost:~$ sudo usermod -m -d dev bob
User@localhost:~$ sudo usermod -m -d infra charlie
User@localhost:~$ sudo usermod -m -d infra dave
```
6.
```console
User@localhost:~$ sudo usermod alice -g dev
User@localhost:~$ sudo usermod bob -g dev
User@localhost:~$ sudo usermod charlie -g infra
User@localhost:~$ sudo usermod dave -g infra
```
7.
```console
User@localhost:~$ sudo chgrp -R dev /home/dev
User@localhost:~$ sudo chgrp -R infra /home/infra
User@localhost:~$ sudo chmod -R 060 /home//home/dev
User@localhost:~$ sudo chmod -R 060 /home/infra 
```
8.
```console
User@localhost:~$ sudo chmod 750 -R /home/dev
User@localhost:~$ sudo chmod 750 -R /home/infra
```
9.
```console
Non, un mot de passe est demandé. Le compte n'a pas encore été activé.
```
10.
```console
User@localhost:~$ sudo passwd alice
  New password : alice
  Retype new password : alice
User@localhost:~$ su alice
```
11.
```console
User@localhost:~$ id alice
uid=1002(alice). gid=1002(dev) groups=1002(dev)
```
12.
```console
User@localhost:~$ getent passwd 1003
Il s'agit de bob.
```
13.
```console
User@localhost:~$ grep dev /etc/group
L'id du groupe dev est 1002.
```
14.
```console
User@localhost:~$ grep 1002 /etc/group
Il s'agit du groupe dev.
```
15.
```console
User@localhost:~$ sudo gpasswd -d charlie infra
Reloving user charlie from group infra
Si l'on regarde les id de charlie, on voit qu'il appartient toujours au groupe infra.
```
16.
```console
User@localhost:~$ sudo chage dave -E 2021-06-01
User@localhost:~$ sudo chage dave -M 90 
User@localhost:~$ sudo chage dave -m 5
User@localhost:~$ sudo chage dave -W 14
User@localhost:~$ sudo chage dave -I 30
```
17.
```console
L'interpreteur de commande root est /bin/bash.
```
18.
```console
Il correspond à un utilisateur sans droit, qui permet d'éxecuter quelque chose sans conséquence sur le reste.
```
19.
```console
Le mot de passe est mémorisé 15 minutes par la commande sudo.
Il s'agit de la commande sudo -k.
```

**Exercice 2**

1. 
```console
User@localhost:/home$ sudo mkdir test
User@localhost:/home/test$ sudo touch fichier.txt
```
2. 
```console
User@localhost:/home/test$ sudo chmod 000 fichier.txt
Conclusion : root peut toujours l'ouvrir. 
```
3. 
```console
User@localhost:/home/test$ echo "echo Hello" > fichier
Les droits seront les mêmes que ceux du fichier.
```
4. 
```console
On peut executer le fichier dans les 2 cas.
```
5. 
```console
Si nous n'avons aucun droit dans le repertoire, il est impossible d'y voir son contenu, d'ecrire/lire sur ses fichiers existants.
```
6. 
```console
La suppression d'un fichier dépend des permissions du dossier et non pas des permissions du fichiers
```
7. 
```console
Si l'on enleve le droit d'execution, on ne peut plus modifier ni rentrer dans le dossier correspondant
```
8. 
```console
On ne peut sortir du repertoire.
Grace a cd .. on peut y en sortir, car cette commande ne depend pas du repertoire ou l'on se trouve
```
9. 
```console
User@localhost:/home/test$ chmod +x ./
User@localhost:/home/test$ chmod 751 fichier.txt
```
10. 
```console
umask = 277
```
11. 
```console
umask = 022 (fichiers)
umask = 266 (dossier)
```
12. 
```console
umask = 057
umask = 046
```
13. 
```console
1) umask 136
2) umask 2 2 4
3) --x r-- -w-
4) umask 1 3 6
```
14. 
```console
Tout le monde peut lire /etc/passwd
Les mots de passe étant cryptés, ce n'est pas grave si tout le monde a acces a ce fichier
```
15. 
```console
Access Control Lists (a faire plus tard)
```
16. 
```console
Quotas disques (a faire plus tard)
```
