Kasutasin Wordpress'i installeerimiseks järgmist juhendit: http://www.teixeira-soft.com/bluescreen/2016/03/15/gnulinux-how-to-install-wordpress-on-debian-8-jessie-blue-screen/
#
Üritasin "user-friendly" URL loomiseks paigaldada BIND9, mis ka õnnestus, kuid kuna mul on keelatud muuta võrguinterface'i seadeid kooliarvuti Windows'is, siis paraku ma sellest tõestuseks pilte teha ei saanud.
#
1. Lõin Wordpress'i databaasi: mysql -u root -p
#
2. Kasutasin käske: CREATE DATABASE wpdatabase;
CREATE USER wpuser@localhost IDENTIFIED BY 'qwerty'; 
GRANT ALL PRIVILEGES ON wpdatabase.* TO wpuser@localhost; 
FLUSH PRIVILEGES; 
exit
#
3. Restartisin service'id: service apache2 restart, service mysql restart
#
4. Tõmbasin alla kõige uuema Wordpress'i ja pakkisin paki lahti: 
cd /tmp, 
wget -c http://wordpress.org/latest.zip, 
unzip -q latest.zip -d /var/www/html
#
5. Seadistasin kaustade õigused: chown -R www-data.www-data /var/www/html/wordpress, 
chmod -R 755 /var/www/html/wordpress, 
mkdir -p /var/www/html/wordpress/wp-content/uploads, 
chown -R www-data.www-data /var/www/html/wordpress/wp-content/uploads
#
6. Lõin konfiguratsioonifaili sample-failist: cd /var/www/html/wordpress/, cp wp-config-sample.php wp-config.php
#
7. Konfigureerisin wp-config.php faili vastavalt juhendile.
#
8. Läksin aadressile ip/wordpress.
 



