# Instalar agente SNMP
sudo apt-get install snmpd -y
sudo nano /etc/snmp/snmpd.conf

sudo ufw allow 161/udp
sudo ufw status

sudo systemctl restart snmpd
sudo systemctl enable snmpd

