# shinken-pack-collectd-redis

## Description

This Shinken monitoring pack is used to manage redis services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work

## Objects

### Templates

#### Host templates

* collectd-redis: Manage all default thresholds and values for services

### Services

| Service name                               | Description                        | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|--------------------------------------------|------------------------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| Redis - $KEY$ processes                    | Check Redis processes              | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _redis_processes           |
| Redis - $KEY$ listen                       | Check Redis port listening         | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _redis_listen              |
| Redis - $KEY$ - Total connections          | Check total connections            | redis-$VALUE1$/total_connections               | value     | none          | $VALUE2$         | $VALUE3$          | _redis_databases           |
| Redis - $KEY$ - Blocked clients            | Checks blocked clients             | redis-$VALUE1$/blocked_clients                 | value     | none          | $VALUE4$         | $VALUE5$          | _redis_databases           |
| Redis - $KEY$ - Uptime                     | Checks uptime                      | redis-$VALUE1$/uptime                          | value     | none          | $VALUE6$         | $VALUE7$          | _redis_databases           |
| Redis - $KEY$ - Current client connections | Checks current clients connections | redis-$VALUE1$/current_connections_clients     | value     | none          | $VALUE8$         | $VALUE9$          | _redis_databases           |
| Redis - $KEY$ - Total operations           | Checks total operations            | redis-$VALUE1$/total_operations                | value     | none          | $VALUE10$        | $VALUE11$         | _redis_databases           |

## Default values

    _redis_databases    localhost $(1)$$(1)$$(1:)$$(1:)$$(1:)$$(1:)$$(5)$$(10)$$(256)$$(512)$
    _redis_processes    redis server $(redis-server)$$(1:1)$$(1:1)$
    _redis_listen       Listen 6379 $(6379)$$(1:1)$$(1:1)$
