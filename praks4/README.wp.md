1. Lubasin Apache SSL mooduli: a2enmod ssl
#
2. Aktiveerisin default veebisaidi: a2ensite default-ssl
#
3. Apache2 reload: service apache2 reload
#
4. Lõin uue kataloogi, kuhu võib lisada privaatvõtme ja sertifikaadi: mkdir /etc/apache2/ssl
#
5. Kasutasin käsku ja täitsin vastavalt juhendile kohad: openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt
#
6. Lisasin failiõigused, millega kaitsen oma privaatvõtit ja sertifikaati: chmod 600 /etc/apache2/ssl/*
#
7. Konfigureerisin nano /etc/apache2/sites-enabled/default-ssl.conf:
ServerName 172.23.13.37:443, SSLCertificateFile /etc/apache2/ssl/apache.crt, SSLCertificateKeyFile /etc/apache2/ssl/apache.key
#
8. service apache2 reload
#
9. openssl s_client -connect your_server_ip:443
