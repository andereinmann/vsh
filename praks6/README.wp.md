#
**WORDPRESSI INSTALLEERIMINE & DATABAASI JOOKSUTAMINE TEISEST VIRTUAALMASINAST**

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
2. Jooksutasin skripti, millega sain seadistada "root" kasutaja salasõna ning eemaldasin ebavajalikud teenused:
```
mysql_secure_installation
```
3. Lisasin veebiserveri IP lubatud remote ühenduste juurde (faili asukoht on minu virtuaalmasinas on "/etc/mysql/mysql.conf.d/mysqld.cnf"):
```
bind-address    = 10.0.2.4
```

**Jälle veebiserveris:**

1. Installeerisin MariaDB-client ja PHP-mysql paketid:
```
apt update
apt install mariadb-client php-mysql
```
2. Testisin remote loginit uue remote kasutajaga:
```
mysql -u wpuser -h 10.0.2.4 -p
status;
exit
```
3. Konfigureerisin Wordpress'i Databaasiga ühendamiseks:
```
cd /var/www/html/wordpress/
cp wp-config-sample.php wp-config.php
```
4. "wp-config.php" faili sisu:
```
/** The name of the database for WordPress */
define('DB_NAME', 'wordpress');

/** MySQL database username */
define('DB_USER', 'wpuser');

/** MySQL database password */
define('DB_PASSWORD', 'qwerty');

/** MySQL hostname */
define('DB_HOST', '10.0.2.5');
```
