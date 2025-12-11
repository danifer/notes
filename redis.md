Redis commands for bulk delete keys, find keys with no TTL expiration, and pattern matching operations.

---

Find keys with no expiration date:
    redis-cli -n 3 keys  "*" | while read LINE ; do TTL=`redis-cli ttl $LINE`; if [ $TTL -eq -1 ]; then echo "$LINE"; fi; done;

Bulk delete redis keys:
    redis-cli keys  "*" | while read LINE; do redis-cli del $LINE; done;

Bulk delete keys from a Redis store with intermittent pauses.
    redis-cli keys "*" | while read LINE; do NUM=$[$NUM+1]; if [ $NUM -ge 5000 ]; then echo sleeping; sleep 10; NUM=0; else redis-cli -n 3 del $LINE; fi; done;

Run Redis commands on all keys matching a pattern.
    redis-cli -n 3 keys "*" | while read LINE; do NUM=$[$NUM+1]; redis-cli -n 3 ttl $LINE; done;
