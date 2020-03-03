# AutoCertificat

AutoCertif est un script bash permettant la génération de certificats auto-signés. Lors de l'exécution du script, une architecture de fichiers est créée pour pouvoir recevoir les différents fichiers.
Un fichier **certificat.cfg** est à générer `sudo ./autoCertif init` puis à compléter afin de générer le certificat avec les informations nécessaires. Les fichiers générés sont automatiquement déplacés au sein de l’architecture d’apache. Les différents modules sont automatiquement activés et les différents fichiers de configuration sont mis à jour.
Un hôte virtuel est initialisé sur le port 443 pour accueillir une connexion https. Il suffit finalement d’importer le certificat généré sur le navigateur.

# Auteurs

- Froissart Kévin

      mailto: kevin.froissart.etu@univ-lille.fr

- Bourdin Maxence

      		mailto: maxence.bourdin2.etu@univ-lille.fr

# Prérequis

Le fichier **openssl.cnf** doit être présent à la racine du projet.

```
cp "$(locate openssl.cnf)" chemin/openssl.cnf
```

Pouvoir executer en sudo.

Avoir modifié le fichier certificat.cfg.

# Utilisation

```
chmod +x ./autoCertif

sudo ./autoCertif

sudo ./autoCertif clean

sudo ./autoCertif init

sudo ./autoCertif --help

```

# Difficultés rencontrées:

La première difficultée a été de choisir entre utiliser du bash, java ou expect afin d’automatiser notre processus. Certaines parties comme la lecture/modification de fichiers ou la gestion de paramètres aurait été plus simple en java. L'exécution de commandes système sont bien évidemment plus simple à exécuter en bash et l’automatisation des réponses à ces commandes doit être faite en expect.

Nous avons alors choisi d’utiliser du bash, d’apprendre à gérer nos paramètres et nos fichiers en bash.

Afin d’automatiser les réponses aux commandes exécutées nous avons eu besoin d’utiliser expect. Nous avons alors trouvé une solution afin d’utiliser du code expect dans notre code bash qui ne sont pas compatibles de base. Nous pouvons intégrer notre code expect à notre code bash en utilisant `<<EOD`

### Nous avons aussi rencontré d’autres difficultés:

- Pas de droit sudo sur les machines de l’université

- Pas tous les packages présents (expect)

- Pas “apt” sur les machines virtuelles

- Pas assez de quota pour faire d’autres machines virtuelles

**Solution** -> amener sa propre machine

# Ce que nous avons appris:

- Utiliser des fonctions et gérer des variables en bash

- Lire et parser un fichier avec awk

- Utiliser sed pour écrire dans un fichier

- Utiliser expect

- Utilisation de fonctions récursives

- Localisation de fichiers avec locate

- Utilisation plus spécifique des paramètres pour chacune des commandes ci-dessus

- Génération de paire de clés et certificats avec openssl

# Ce qui fonctionne pour le moment:

Création automatique d’un certificat auto-signé, mise à jour des fichiers de configuration d’apache, activation des modules, éditions des ports et hôtes virtuels.

# Comment exécuter le script:

Package nécessaire : apache2 openssl expect

    sudo apt-get install apache2 openssl expect

Il vous sera proposé de les installer lors de l'exécution du script s’ils ne le sont pas.

Exécutez `chmod +x ./autoCertif` afin de rendre le fichier exécutable.

Exécutez `sudo ./autoCertif --help` pour recevoir des informations complémentaires.

Exécutez `sudo ./autoCertif init` pour créer le fichier obligatoire certificat.cfg.

Exécutez `sudo ./autoCertif clean` pour détruire l’architecture de fichier créée par le script.

Exécutez `sudo ./autoCertif` afin de créer le certificat.

Il est nécessaire d’avoir au préalable rempli le fichier certificat.cfg avant d'exécuter le script.

S’il n’est pas présent exécutez `sudo ./autoCertif init`

Un fichier de configuration **openssl.cnf** est aussi fourni et requis.
