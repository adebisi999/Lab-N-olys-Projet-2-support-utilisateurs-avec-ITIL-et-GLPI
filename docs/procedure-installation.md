# Procédure d'installation de GLPI 12 sur Debian 13

## 1. Serveur
- Clone du modèle Debian du projet 1, nommé `srv-glpi`, sur le réseau interne `LAN-Neolys`.
- Nom d'hôte et identité :
```bash
sudo hostnamectl set-hostname srv-glpi
sudo sed -i 's/debian-template/srv-glpi/g' /etc/hosts
sudo systemd-machine-id-setup
```
- IP fixe (un serveur ne doit pas changer d'adresse) :
```bash
sudo nmcli con mod "Wired connection 1" ipv4.addresses 10.10.10.10/24
sudo nmcli con mod "Wired connection 1" ipv4.gateway 10.10.10.1
sudo nmcli con mod "Wired connection 1" ipv4.dns 10.10.10.1
sudo nmcli con mod "Wired connection 1" ipv4.method manual
sudo nmcli con up "Wired connection 1"
```

## 2. Pile LAMP
```bash
sudo apt install -y apache2 mariadb-server openssh-server
sudo apt install -y php php-mysql php-curl php-gd php-intl
sudo apt install -y php-xml php-mbstring php-zip php-bz2 php-ldap php-bcmath
```

## 3. Base de données
```bash
sudo mariadb-secure-installation
sudo mariadb
```
```sql
CREATE DATABASE glpi CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'glpi'@'localhost' IDENTIFIED BY '********';
GRANT ALL PRIVILEGES ON glpi.* TO 'glpi'@'localhost';
FLUSH PRIVILEGES;
```
Compte dédié, limité à la base `glpi` (moindre privilège).

## 4. GLPI
```bash
cd /tmp
wget https://github.com/glpi-project/glpi/releases/download/12.0.2/glpi-12.0.2.tgz
sudo tar -xzf glpi-12.0.2.tgz -C /var/www/
sudo chown -R www-data:www-data /var/www/glpi
```

## 5. Apache
`/etc/apache2/sites-available/glpi.conf` :
```apache
<VirtualHost *:80>
    ServerName glpi.neolys.lan
    DocumentRoot /var/www/glpi/public
    <Directory /var/www/glpi/public>
        Require all granted
        RewriteEngine On
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^(.*)$ index.php [QSA,L]
    </Directory>
</VirtualHost>
```
Seul le dossier `public` est exposé : la configuration et les identifiants de la base restent hors de la racine web.
```bash
sudo a2enmod rewrite
sudo a2dissite 000-default
sudo a2ensite glpi
sudo apachectl configtest
sudo systemctl reload apache2
```

## 6. Installation web, puis sécurisation
- Assistant sur `http://10.10.10.10`, avec la base `glpi` et l'utilisateur `glpi`.
- Compte administrateur nominatif `adm-neolys` (Super-Admin), puis désactivation des comptes `glpi` et `normal`, et changement des mots de passe de `tech` et `post-only`.
- Suppression du fichier d'installation : `sudo rm /var/www/glpi/install/install.php`
- Dans `/etc/php/8.4/apache2/php.ini` : `session.cookie_httponly = On` et `date.timezone = Europe/Paris`

## 7. Inventaire
- GLPI : Administration › Inventaire › activer, avec une authentification **Basic**.
- **Windows** : GLPI Agent `.msi`, cible `http://10.10.10.10/`, identifiants dans `HKLM\SOFTWARE\GLPI-Agent` (valeurs `user` et `password`).
- **Linux** :
```bash
wget https://github.com/glpi-project/glpi-agent/releases/download/1.21/glpi-agent-1.21-linux-installer.pl
sudo perl glpi-agent-1.21-linux-installer.pl --server=http://10.10.10.10/ --runnow
# Identifiants de l'inventaire
sudo nano /etc/glpi-agent/conf.d/auth.cfg     # user = ... / password = ...
sudo chmod 600 /etc/glpi-agent/conf.d/auth.cfg
sudo glpi-agent --force
```
