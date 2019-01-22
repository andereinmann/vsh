#
**DokuWiki INSTALLEERIMINE VEEBISERVERISSE**


**Veebiserveris:**

1. Installeerisin paketid: 
```
sudo apt install -y dokuwiki
```

2. Seadistasin kaustad ümber: 
```
ln -s /usr/share/dokuwiki /var/www/html/
```

3. Sisestasin käsu:
```
su -c 'cat <<EOF > /etc/apache2/sites-available/dokuwiki.conf
<VirtualHost _default_:443>
  SSLEngine on
  SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
  SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key

  <Directory /usr/share/dokuwiki>
    Order allow,deny
    Allow from all
  </Directory>
</VirtualHost>
EOF
'
```

4. Restart: 
```
  sudo a2enmod ssl
  sudo a2ensite dokuwiki
  sudo systemctl restart apache2
```

5. Sisenesin Wiki lehele (vajalik oli ette sisestada "HTTPS://": 
```
https://<ip>/dokuwiki
```



