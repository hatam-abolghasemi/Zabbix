# ZABBIX CLICKHOUSE MONITORING


**DISCLAIMER: THIS TEMPLATE IS A MIXTURE OF SEVERAL DIFFERENT SOURCES THAT I'VE LEARNED ABOUT CLICKHOUSE MONITORING. I HAVE NOT BUILD THIS TEMPLATE FROM SCRATCH. REFERENCES ARE MENTIONED AT THE BOTTOM.**

So ClickHouse 

**TABLE OF CONTENTS**
1. [Updates](#1-updates)
2. [Implementation](#2-implementation)
3. [References](#3-references)

## 1. Updates

[23.04.07](#230407)

### 23.04.07:

* ADD service:
    * ADD **`systemd.unit.get[clickhouse-server.service]`**
    * ADD `systemd.service.uptime[clickhouse-server.service]`
    * ADD `systemd.service.active_state[clickhouse-server.service]`
* ADD metrics:
    * ADD **`clickhouse.system.metrics`**
    * ADD `clickhouse.merge.current`
    * ADD `clickhouse.delayed.inserts`
    * ADD `clickhouse.distributed.files.to.insert`
    * ADD `clickhouse.http.connection`
    * ADD `clickhouse.memory.tracking`
    * ADD `clickhouse.mysql.connection`
    * ADD `clickhouse.part.mutations`
    * ADD `clickhouse.tcp.connections`
    * ADD `clickhouse.replicas.readonly.total`
* ADD events:
    * ADD **`clickhouse.system.events`**
    * ADD `clickhouse.compressed.read.buffer.bytes`
    * ADD `clickhouse.inserted_rows.rate`
    * ADD `clickhouse.mark.cache.hits`
    * ADD `clickhouse.mark.cache.misses`
    * ADD `clickhouse.merge_rows.rate`
    * ADD `clickhouse.insert_query.rate`
    * ADD `clickhouse.query.rate`
    * ADD `clickhouse.select_query.rate`
    * ADD `clickhouse.read_bytes.rate`
    * ADD `clickhouse.selected.marks`
    * ADD `clickhouse.selected.parts`
* ADD asynchronous metrics:
    * ADD **`clickhouse.system.asynchronous_metrics`**
    * ADD `clickhouse.mark.cache.files`
    * ADD `clickhouse.max.part.count.for.partition`
    * ADD `clickhouse.network.receive.errors`
    * ADD `clickhouse.network.send.errors`
    * ADD `clickhouse.replicas.max.inserts.in.queue`
    * ADD `clickhouse.replicas.max.merges.in.queue`
    * ADD `clickhouse.replicas.max.queue.size`
    * ADD `clickhouse.replicas.max.absolute.delay`
    

---

## 2. Implementation

Step 1. Create a user in clickhouse for monitoring.

Step 2. Link "ClickHouse" template to its host.

Step 3. Fill `{$CLICKHOUSE.USER}` and `{$CLICKHOUSE.PASSWORD}` macros with the user credentials you just made.

---

## 3. References

1. [Zabbix Official Template](https://www.zabbix.com/integrations/clickhouse)
2. [ClickHouse Docs Monitoring](https://clickhouse.com/docs/en/operations/monitoring/)
3. [Altinity ClickHouse Template](https://github.com/Altinity/clickhouse-zabbix-template)
4. [Altinity YouTube](https://www.youtube.com/watch?v=W9KlehhgwLw)
