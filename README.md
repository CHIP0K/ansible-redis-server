Redis Server
=========

Install redis-server from the redis repository packages.redis.io and prometheus exporter and enable zabbix-agent2 plugin if needed

Role Variables
--------------

Available defined default variables in this role:

```yaml
redis_port: "6379"  # Default Redis port 
redis_logfile: "/var/log/redis/redis-server.log"  # Default path redis-server log file
redis_dbfilename: "dump.rdb"  # Default Redis database file
redis_maxmemory: "100mb"
redis_maxmemory_policy: "allkeys-lru"
redis_user: "redis"
redis_group: "redis"

# Monitoring tools
prometheus_redis_exporter: false # Prometheus exporter for Redis
zabbix_redis_plugin: false # Zabbix plugin for Redis
```

Available Variables is not defined by default:

```yaml
redis_bind_local_interface: ["eth0", "eth1"] # This is the interface that the Redis server will bind to
redis_requirepass: "password" # This is a secret, so it should be defined in the inventory file
redis_server_monitoring_user: # This is user for monitoring Redis server (e.g. prometheus-redis-exporter)
  username: "monitoring" # This is a user for monitoring Redis server
  password: "password" # This is a password for monitoring Redis server
redis_server_users: # This is a list of users for Redis server
  - username: "user"
    password: "password"
```

Example Playbook
----------------

```yaml
- hosts:
    - redis-server-host-or-group
  gather_facts: True
  roles:
    - { role: redis-server }
```

License
-------

BSD

Author Information
------------------

