Kasutasin PHP (7.2, 7.1 & 5.6 versioonide) installeerimiseks järgmiseid käske:
apt update
apt upgrade

sudo apt install ca-certificates apt-transport-https
wget -q https://packages.sury.org/php/apt.gpg -O- | apt-key add -
echo "deb https://packages.sury.org/php/ jessie main" | tee /etc/apt/sources.list.d/php.list

apt install php7.2
apt install php7.2-cli php7.2-common php7.2-curl php7.2-gd php7.2-json php7.2-mbstring php7.2-mysql php7.2-xml

apt install php7.1
apt install php7.1-cli php7.1-common php7.1-curl php7.1-gd php7.1-json php7.1-mbstring php7.1-mysql php7.1-xml

apt install php5.6
apt install php5.6-cli php5.6-common php5.6-curl php5.6-gd php5.6-json php5.6-mbstring php5.6-mysql php5.6-xml
