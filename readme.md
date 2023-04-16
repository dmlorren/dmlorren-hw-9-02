# Домашнее задание к занятию "`9.2 «Система мониторинга Zabbix»`" - `Иванов Дмитрий`

### Задание 1

![Скриншот-1](https://github.com/dmlorren/dmlorren-hw-9-02/blob/main/img/zabbix1.jpg)
![Скриншот-2](https://github.com/dmlorren/dmlorren-hw-9-02/blob/main/img/zabbix2.jpg)


### Используемые команды

```
wget https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix-release/zabbix-release_6.4-1+debian11_all.deb
sudo dpkg -i zabbix-release_6.4-1+debian11_all.deb
sudo apt update
sudo apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
sudo apt install postgresql
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
sudo nano /etc/zabbix/zabbix_server.conf
sudo sed -i 's/# DBPassword=/DBPassword=123456/g' /etc/zabbix/zabbix_server.conf
sudo systemctl restart zabbix-server zabbix-agent apache2
sudo systemctl enable zabbix-server zabbix-agent apache2
sudo systemctl status zabbix-server
sudo  systemctl status zabbix-agent
sudo  systemctl status apache2
cat /var/log/zabbix/zabbix_server.log
```

### Задание 2

![Скриншот-3](https://github.com/dmlorren/dmlorren-hw-9-02/blob/main/img/zab_ex2_md1.jpg)
![Скриншот-4](https://github.com/dmlorren/dmlorren-hw-9-02/blob/main/img/zab_ex2_md2.jpg)
![Скриншот-5](https://github.com/dmlorren/dmlorren-hw-9-02/blob/main/img/zab_ex_md3.jpg)

### Используемые команды к заданию 2

```
sudo wget https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix-release/zabbix-release_6.4-1+debian11_all.deb
sudo dpkg -i zabbix-release_6.4-1+debian11_all.deb
sudo apt update
sudo apt install zabbix-agent
sudo systemctl restart zabbix-agent
sudo systemctl enable zabbix-agent
sudo  systemctl status zabbix-agent
sudo nano /etc/hosts
nano /etc/zabbix/zabbix_agentd.conf 
sudo systemctl status zabbix-agent.service
sudo systemctl restart zabbix-agent.service
sudo systemctl status zabbix-agent.service
sudo tail -f -n30 /var/log/zabbix/zabbix_agentd.log

Дополнительно потребовалось внести изменения в zabbix_agentd.conf
sudo nano /etc/zabbix/zabbix_agentd.conf
Server=127.0.0.1,158.160.12.153,158.160.0.41,10.129.0.8,10.129.0.4
```
