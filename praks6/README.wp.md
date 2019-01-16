#
**WORDPRESSI INSTALLEERIMINE**

**Veebiserveris:**

1. Installeerisin paketid: 
```
apt-get install apache2 mysql-client mysql-server php5 php5-mysql php5-curl php5-gd
```
Vahepeal tuli sisestada MySQL "root" kasutaja parool.


2. Taaskäivitasin Apache2: 
```
service apache2 restart
```
Taaskäivitasin MySQL'i: 
```
service mysql restart
```

3. Installeerisin Wordpress'i:
```
cd /tmp

wget -c http://wordpress.org/latest.zip

unzip -q latest.zip -d /var/www/html/
```

4. Sätestasin Wordpress'i kataloogidele õiguseid ning lisasin vajalikud juurde: 
```
chown -R www-data.www-data /var/www/html/wordpress

chmod -R 755 /var/www/html/wordpress

mkdir -p /var/www/html/wordpress/wp-content/uploads

chown -R www-data.www-data /var/www/html/wordpress/wp-content/uploads
```

**DB serveris:**

1. Installeerisin MariaDB:
```
apt install mariadb-server
```
2. Jooksutasin skripti, millega sain seadistada "root" kasutaja salasõna ning eemaldasin ebavajalikud teenused.
```
mysql_secure_installation
```
