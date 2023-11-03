*********************************************
       Carsten Rieger IT-Services
        https://www.c-rieger.de
*********************************************

# Nextcloud Installationsskript // Nextcloud Installation script
D: Installieren Sie Ihren eigenen Nextcloud-Server in weniger als 10 Minuten.<br>
E: Install your own Nextcloud server in less than 10 minutes.

* <b>Ubuntu 20.04</b> LTS [AMD x86_64] <sup>deprecated/veraltet</sup> / <b>22.04 LTS</b> [AMD x86_64] / <b>Debian 11.x</b> [AMD x86_64] / <b>Debian 12</b> [AMD x86_64] 
<br>Proxmox LXC-support<b></b><br>
<small>(Be aware, Debian requires a Proxmox-option called 'nesting=1')</small><br>
* NGINX ≥ 1.25 from nginx
* Auswahl / Option: PHP 8.2 // PHP 8.1 // PHP 8.0
* Auswahl / Option: MariaDB 10.11 // postgreSQL 15
* Auswahl / Option: Self-signed // Let's Encrypt certificates
* Auswahl / Option: Nextcloud Release ≥ 25.0.7<br>
* Auswahl / Option: Nextcloud Office/OnlyOffice
* etc...

<h2>INSTALLATION (Ubuntu/Debian):</h2>
<h3>D/E: Vorbereitungen/Preparations:</h3>
<code>sudo -s</code><br>
<code>wget -O zero.sh wget -O zero.sh https://codeberg.org/criegerde/nextcloud-zero/raw/branch/master/<debian/ubuntu>.sh</code><br>
<code>chmod +x zero.sh</code><br> <br>
<h3>D/E: Konfigurationsvariablen anpassen / modify configuration variables:</h3></code>
<code>nano zero.sh</code><br> <br>
<code>##################################################
# D: Konfigurationsvariablen - bitte anpassen!   #
# E: Configuration variables - please configure! #
##################################################

NEXTCLOUDDATAPATH="/data"
NEXTCLOUDADMINUSER="nc_admin"
NCRELEASE="latest.tar.bz2"
PHPVERSION="8.2"
LETSENCRYPT="n"
NEXTCLOUDDNS="ihre.domain.de"
DATABASE="m"
NCDBUSER="ncdbuser"
CURRENTTIMEZONE='Europe/Berlin'
PHONEREGION='DE'
NEXTCLOUDOFFICE="n"
ONLYOFFICE="n"
UPLOADSIZE='10G'
APTIP4="n"
RESOLVER="176.9.93.198 176.9.1.117"</code><br>
Optional:<br><code>MARIADBROOTPASSWORD=$(openssl rand -hex 16)
NCDBPASSWORD=$(openssl rand -hex 16)
NEXTCLOUDADMINUSERPASSWORD=$(openssl rand -hex 16)
REDISPASSWORD=$(openssl rand -hex 16)
NEXTCLOUDEXTIP=$(dig +short txt ch whoami.cloudflare @1.0.0.1 | tr -d \")</code><br>

<h3>Installation:</h3>
<code>./zero.sh</code>
<h2>D/E: DEINSTALLATION/UNINSTALL:</h2>
D. Sofern Sie das Skript erneut ausführen möchten, so führen Sie bitte zuerst die Deinstallation durch:<br>
E: If you want to re-install your server - please uninstall your software first.<br> <br>
<code>/home/*benutzer*/Nextcloud-Installationsskript/uninstall.sh</code><br>
<code>rm -f /home/*benutzer*/Nextcloud-Installationsskript/uninstall.sh</code><br> <br>
D: Dabei werden alle Softwarepakete (inkl. DB) sowie alle Verzeichnisse und Daten aus der vorherigen Installation entfernt. Im Anschluss daran kann die Installation erneut durchgeführt werden.<br>
E: All data, databases and software from the previous installation will be removed. Afterwards you can re-run the installation script.<br>
<h2>D/E: ERNEUTE INSTALLATION/RE-INSTALLATION:</h2>
<code>./zero.sh</code><br>
<h2>D/E: LOGDATEI/LOGFILE:</h2>
<code>nano /home/*benutzer*/Nextcloud-Installationsskript/install.log</code><br>

-----------------------------------------------------------------------------------

D: Weitere Optimierungs-, Härtungs- und Erweiterungsmöglichkeiten finden Sie hier:<br>
E: Further hardening, optimization and enhancement information can be found here:<br>&nbsp;<br>
https://www.c-rieger.de/nextcloud-installationsanleitung/<br>&nbsp;<br>
Carsten Rieger IT-Services
