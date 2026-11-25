# Journal de dépannage – Projet 2 (GLPI)

### 1. `nmcli` : « la valeur de l'argument ipv4.method est requise »
- **Cause** : la commande était trop longue et a été coupée au moment de la saisie.
- **Solution** : la découper en une commande par paramètre (adresses, passerelle, DNS, méthode).
- **Leçon** : sur une console sans copier-coller, préférer des commandes courtes, puis passer en SSH.

### 2. Paquets PHP introuvables
- **Cause** : fautes de frappe (`phpp-gd`, `phpo-zip`).
- **Solution** : relire la commande et découper les longues listes de paquets.

### 3. GLPI : « L'extension mysqli est absente »
- **Cause** : l'installation de `php-mysql` avait échoué, avec la même ligne de commande que les fautes de frappe.
- **Diagnostic** : `php -m | grep -i mysql` ne renvoyait rien.
- **Solution** : `sudo apt install php-mysql`, puis `systemctl restart apache2`.

### 4. Pas de copier-coller dans la console VirtualBox
- **Cause** : le presse-papiers partagé exige une interface graphique, alors que les serveurs sont en mode console.
- **Solution** : administration en **SSH** depuis le poste Windows 11 (`ssh admin-neolys@10.10.10.10`), comme en entreprise.

### 5. La VM Windows bloquée sur « BdsDxe: failed to load Boot0001 UEFI VBOX CD-ROM »
- **Cause** : l'ordre d'amorçage plaçait le lecteur optique, vide, en premier.
- **Solution** : mettre le disque dur en premier et décocher le lecteur optique.

### 6. `apt install glpi-agent` : paquet introuvable
- **Cause** : l'agent GLPI n'est pas dans les dépôts Debian.
- **Solution** : l'installateur officiel `glpi-agent-1.21-linux-installer.pl`, téléchargé depuis GitHub.

### 7. Agent : « authentication required, no credentials available »
- **Cause** : l'inventaire de GLPI exige une authentification, ce qui est une bonne pratique : sans elle, n'importe quelle machine peut injecter de faux inventaires.
- **Solution** : authentification **Basic** dans GLPI, identifiants dans `/etc/glpi-agent/conf.d/auth.cfg` (en `chmod 600`) sous Linux, et dans le registre sous Windows.

### 8. Heures décalées d'une heure dans GLPI
- **Cause** : le fuseau horaire de PHP était resté sur UTC.
- **Impact** : des échéances de SLA fausses.
- **Solution** : `date.timezone = Europe/Paris` dans `php.ini`, et le fuseau dans Configuration › Générale.

### 9. Mauvais tickets liés au problème
- **Cause** : les identifiants GLPI étaient décalés de 1 par rapport à la liste de travail, parce que le ticket de test avait pris le n° 1.
- **Solution** : vérifier le **titre**, et pas seulement le numéro, avant de lier des objets.
- **Leçon** : toujours se fier au contenu, pas à un identifiant supposé.
