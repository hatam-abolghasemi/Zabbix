# ZABBIX BIND9 MONITORING


**TABLE OF CONTENTS**
1. [Implementation](#1-implementation)
2. [History](#2-history)

---

## 1. Implementation


1. **Configure userparameter.**

    `cd /etc/zabbix/zabbix_agent2.d/ && mkdir userparameters && cd userparameters/`

* Copy the `bind.conf` file to the `userparameters` directory you just made.
    * There is an issue with the first time creation of `named.stats` file. You need to edit `bind.conf` like this:
        ```
        UserParameter=bind9.bulk, echo "" > /var/cache/bind/named.stats && rndc stats && cat /var/cache/bind/named.stats
        ```

* Add this line to your `zabbix_agent2.conf` file.

    `Include=/etc/zabbix/zabbix_agent2.d/userparameters/*.conf`

* Restart zabbix-agent2 service to apply changes.

    `systemctl restart zabbix-agent2`


2. **Correct bind `named.stats` permissions**

    `usermod -aG bind zabbix && rndc stats && chmod 664 /var/cache/bind/named.stats`


3. **Link "Bind" template to its host.**

* Don't forget to reset the `bind.conf` to its first version and restart the zabbix-agent2 service.

---

## 2. History

[23.04.14](#230414)

### 23.04.14:

* ADD service:
    * ADD **`systemd.unit.get[bind9.service]`**
    * ADD `systemd.service.uptime[bind9.service]`
    * ADD `systemd.service.active_state[bind9.service]`
* ADD statistics:
    * ADD **`bind9.bulk`**
    * ADD `bind.query.timeouts`
    * ADD `bind.incoming.queries.a`
    
---
