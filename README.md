# AutoCertificat

Notre projet consiste à scripter et automatiser complétement le processus de création de certificat pour un serveur Apache.
Nous utiliserons pour cela en priorité du Java et du scripting Bash.

# Auteurs 

* Bourdin Maxence 
mailto: maxence.bourdin2.etu@univ-lille.fr

* Froissart Kévin 
mailto: kevin.froissart.etu@univ-lille.fr

# Prérequis

fichier openssl.cnf présent à la racine du projet

```
cp /usr/local/etc/ssl/openssl.cnf chemin/openssl.cnf
```

Pouvoir executer en sudo
Avoir modifié le fichier certificat.cfg

# Utilisation

```
chmod +x ./autoCertif
sudo ./autoCertif
sudo ./autoCertif clean
sudo ./autoCertif init
sudo ./autoCertif --help
```