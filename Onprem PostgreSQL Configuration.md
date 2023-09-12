# DB Version: 12
# OS Type: linux
# DB Type: oltp
# Total Memory (RAM): 23 GB
# CPUs num: 10
# Connections num: 1000
# Data Storage: ssd

max_connections = 1000
shared_buffers = 5888MB
effective_cache_size = 17664MB
maintenance_work_mem = 1472MB
checkpoint_completion_target = 0.9
wal_buffers = 16MB
default_statistics_target = 100
random_page_cost = 1.1
effective_io_concurrency = 200
work_mem = 1507kB
min_wal_size = 2GB
max_wal_size = 8GB
max_worker_processes = 10
max_parallel_workers_per_gather = 4
max_parallel_workers = 10
max_parallel_maintenance_workers = 4

data_directory = '/[data_dir]/sdb/main'
listen_addresses = '*'
port = 5432
shared_preload_libraries = 'pg_stat_statements'
log_timezone = 'Asia/Jakarta'
timezone = 'Asia/Jakarta'

log_destination = 'stderr'
logging_collector = on
log_directory = '/var/log/postgresql'
log_filename = 'postgresql-%Y-%m-%d.log'
log_file_mode = 0755
log_min_messages = warning
log_min_error_statement = error
log_min_duration_statement = 1000
log_line_prefix = '[H2H Master] %t %d [%a-%u] [%p] %h ~~'
log_timezone = 'Asia/Jakarta'
log_autovacuum_min_duration = 3000
log_rotation_age = 1d

#Replication Setup
wal_level = logical
max_wal_senders = 10
wal_log_hints = on
archive_mode = on
#archive_command = 'cp /[data_dir]/sdb/main/%p /[data_dir]/sdb/archived'
#archive_command = 'cp /[data_dir]/sdb/main/%p /[data_dir]/sdb/archived && barman-wal-archive 10.9.42.6 pg %p'
archive_command = 'barman-wal-archive 10.9.42.6 h2hdb01 %p'
#(script lihat contoh di archive_command postgresql.conf)
#restore_command ='test -f /var/lib/postgresql/12/archivedir/%f && cp -n /var/lib/postgresql/12/archivedir/%f %p'
#hot_standby = on

