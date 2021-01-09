# raspberry_zabbix_agent
Raspberry 4 Zabbix Agent 5.2

- Raspberry 4 4MB
- Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-1025-raspi aarch64)
- zabbix_agentd 5.2

Self compiled from Zabbix source
```
    apt-get install build-essential checkinstall -y
    apt-get install libpcre3 libpcre3-dev
    cd /tmp
    # get Zabbix sources
    wget https://cdn.zabbix.com/zabbix/sources/stable/5.2/zabbix-5.2.3.tar.gz .
    addgroup --system --quiet zabbix
    adduser --quiet --system --disabled-login --ingroup zabbix --home /var/lib/zabbix --no-create-home zabbix
    mkdir -m u=rwx,g=rwx,o= -p /var/lib/zabbix
    chown zabbix:zabbix /var/lib/zabbix
    tar -xvzf zabbix-5.2.3.tar.gz
    cd zabbix-5.2.3/
    ./configure --enable-agent
    make install
    vim /usr/local/etc/zabbix_agentd.conf

    # start agentd
    zabbix_agentd 
```
