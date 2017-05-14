# HomeAssistant

Install MySQL DB

$ sudo apt-get update && sudo apt-get upgrade
$ sudo apt-get install mysql-server && sudo apt-get install mysql-client
$ sudo apt-get install libmysqlclient-dev
$ sudo apt-get install python-dev python3-dev
$ mysql -u root -p
$ CREATE DATABASE dbname;
$ CREATE USER 'dbuser'@'localhost' IDENTIFIED BY 'password';
$ GRANT ALL PRIVILEGES ON dbname.* TO 'dbuser'@'localhost';
$ FLUSH PRIVILEGES;

Test if user works:
$ mysql -u dbuser dbname -p

Switch to HASS env
$ ssh pi@your_raspberry_pi_ip
$ sudo su -s /bin/bash hass
$ source /srv/hass/hass_venv/bin/activate
$ pip3 install --upgrade mysqlclient

Troubleshooting
Install mysqlclient
$ ssh pi@your_raspberry_pi_ip
$ pip3 install mysqlclient

Mysql running?
sudo service mysql status
sudo service mysql start

Add to configuration.yaml

recorder:
  db_url: mysql://dbuser:password@localhost/dbname
DuckDNS

Installation guide
LetEncrypt

Installation guide
After installation:
$ sudo chmod -R 777 /etc/letsencrypt/archive
$ sudo chmod -R 777 /etc/letsencrypt/live
$ sudo chmod -R 777 /etc/letsencrypt/renewal

Renew Lets Encrypt Certificate

Change the Port forward for port 443, from port 8123Home Assistant to port 443 for the RaspberyPi
This is doner via the USG, Port Forward section, not the firewall section in the settings
Stop unifi & home assistant to maximise available memory
 
sudo ./letsencrypt/letsencrypt-auto renew
Once completed, reset the port forward for port 443, back to port 8123 for Home Assistant.

$ cd certbot
$ sudo ./certbot-auto renew --standalone --no-self-upgrade --force-renewal --preferred-challenges http-01
$ sudo reboot

Creation date 31-01-2017
Renewal date 01-05-2017
Upgrade Lets Encrypt & Certificates

$ cd certbot
$ ./certbot-auto renew

Check Validity

$ openssl x509 -in /etc/letsencrypt/live/<domain>/fullchain.pem -text -noout | grep -A2 Validity
