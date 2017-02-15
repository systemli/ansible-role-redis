# ansible-role-redis

[![Build Status](https://travis-ci.org/systemli/ansible-role-redis.svg?branch=master)](https://travis-ci.org/systemli/ansible-role-redis) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-redis-blue.svg)](https://galaxy.ansible.com/systemli/redis/)

Install and maintain [Redis](https://redis.io/) with Ansible. Contains Tests for Travis CI and Vagrant.

## Requirements


Debian (Wheezy/Jessie) or Ubuntu (Trusty/Xenial). Vagrant for local development.

## Role Variables

    # only for debian
    redis_dotdeb_enabled: True
    redis_version: False # for apt pinning
    redis_apt_state: present

    redis_config_bind: "127.0.0.1"
    redis_config_protected_mode: "yes"
    redis_config_port: "6379"
    redis_config_tcp_backlog: "511"
    redis_config_timeout: "0"
    redis_config_tcp_keepalive: "300"
    redis_config_daemonize: "yes"
    redis_config_supervised: "no"
    redis_config_pidfile: "/var/run/redis/redis-server.pid"
    redis_config_loglevel: "notice"
    redis_config_logfile: '/var/log/redis/redis-server.log'
    redis_config_databases: "16"
    redis_config_save:
      - "900 1"
      - "300 10"
      - "60 10000"
    redis_config_stop_writes_on_bgsave_error: "yes"
    redis_config_rdbcompression: "yes"
    redis_config_rdbchecksum: "yes"
    redis_config_dbfilename: "dump.rdb"
    redis_config_dir: "/var/lib/redis"
    redis_config_slave_serve_stale_data: "yes"
    redis_config_slave_read_only: "yes"
    redis_config_repl_diskless_sync: "no"
    redis_config_repl_diskless_sync_delay: "5"
    redis_config_repl_disable_tcp_nodelay: "no"
    redis_config_slave_priority: "100"
    redis_config_appendonly: "no"
    redis_config_appendfilename: '"appendonly.aof"'
    redis_config_appendfsync: "everysec"
    redis_config_no_appendfsync_on_rewrite: "no"
    redis_config_auto_aof_rewrite_percentage: "100"
    redis_config_auto_aof_rewrite_min_size: "64mb"
    redis_config_aof_load_truncated: "yes"
    redis_config_lua_time_limit: "5000"
    redis_config_slowlog_log_slower_than: "10000"
    redis_config_slowlog_max_len: "128"
    redis_config_latency_monitor_threshold: "0"
    redis_config_notify_keyspace_events: '""'
    redis_config_hash_max_ziplist_entries: "512"
    redis_config_hash_max_ziplist_value: "64"
    redis_config_list_max_ziplist_entries: "512"
    redis_config_list_max_ziplist_value: "64"
    redis_config_list_max_ziplist_size: "-2"
    redis_config_list_compress_depth: "0"
    redis_config_set_max_intset_entries: "512"
    redis_config_zset_max_ziplist_entries: "128"
    redis_config_zset_max_ziplist_value: "64"
    redis_config_hll_sparse_max_bytes: "3000"
    redis_config_activerehashing: "yes"
    redis_config_client_output_buffer_limit_normal: "normal 0 0 0"
    redis_config_client_output_buffer_limit_slave: "slave 256mb 64mb 60"
    redis_config_client_output_buffer_limit_pubsub: "pubsub 32mb 8mb 60"
    redis_config_hz: "10"
    redis_config_aof_rewrite_incremental_fsync: "yes"
    # you can add additional configuration with this key
    redis_config_additional: {}

## Download

Download latest release with `ansible-galaxy`

    ansible-galaxy install systemli.redis

## Example Playbook

    - hosts: servers
      roles:
        - systemli.redis
      vars:
        redis_config_bind: "0.0.0.0"

## License

GPL

## Author Information

https://www.systemli.org
