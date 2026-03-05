# Docker Notes — Day 9

## Docker Version

Client:
 Version:           29.2.1

Server: Docker Desktop 4.63.0 (220185)
 Engine:
  Version:          29.2.1


## Hello World Test

```bash
docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.


## Postgres Container

Command used:
```bash
docker run -d \
  --name pg-prework \
  -e POSTGRES_PASSWORD=prework \
  -p 5432:5432 \
  postgres:15-alpine


## Startup Logs

The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 09:16:21.974 UTC [36] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.
waiting for server to start....2026-03-04 09:16:23.786 UTC [42] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 09:16:23.789 UTC [42] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 09:16:23.802 UTC [45] LOG:  database system was shut down at 2026-03-04 09:16:23 UTC
2026-03-04 09:16:23.815 UTC [42] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down...2026-03-04 09:16:23.884 UTC [42] LOG:  received fast shutdown request
.2026-03-04 09:16:23.899 UTC [42] LOG:  aborting any active transactions
2026-03-04 09:16:23.904 UTC [42] LOG:  background worker "logical replication launcher" (PID 48) exited with exit code 1
2026-03-04 09:16:23.909 UTC [43] LOG:  shutting down
2026-03-04 09:16:23.914 UTC [43] LOG:  checkpoint starting: shutdown immediate
2026-03-04 09:16:23.929 UTC [43] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.005 s, sync=0.002 s, total=0.021 s; sync files=2, longest=0.001 s, average=0.001 s; distance=0 kB, estimate=0 kB
2026-03-04 09:16:23.940 UTC [42] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 09:16:24.041 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 09:16:24.041 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 09:16:24.041 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 09:16:24.049 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 09:16:24.062 UTC [56] LOG:  database system was shut down at 2026-03-04 09:16:23 UTC
2026-03-04 09:16:24.075 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 09:21:51.439 UTC [54] LOG:  checkpoint starting: time
2026-03-04 09:21:54.494 UTC [54] LOG:  checkpoint complete: wrote 33 buffers (0.2%); 0 WAL file(s) added, 0 removed, 0 recycled; write=3.027 s, sync=0.009 s, total=3.056 s; sync files=10, longest=0.004 s, average=0.001 s; distance=151 kB, estimate=151 kB


## Stop and Restart

1. docker stop output:
   pg-prework
2. docker restart output:
   pg-prework
3. docker logs (after restart):
   This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-04 09:16:21.974 UTC [36] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.
waiting for server to start....2026-03-04 09:16:23.786 UTC [42] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 09:16:23.789 UTC [42] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 09:16:23.802 UTC [45] LOG:  database system was shut down at 2026-03-04 09:16:23 UTC
2026-03-04 09:16:23.815 UTC [42] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down...2026-03-04 09:16:23.884 UTC [42] LOG:  received fast shutdown request
.2026-03-04 09:16:23.899 UTC [42] LOG:  aborting any active transactions
2026-03-04 09:16:23.904 UTC [42] LOG:  background worker "logical replication launcher" (PID 48) exited with exit code 1
2026-03-04 09:16:23.909 UTC [43] LOG:  shutting down
2026-03-04 09:16:23.914 UTC [43] LOG:  checkpoint starting: shutdown immediate
2026-03-04 09:16:23.929 UTC [43] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.005 s, sync=0.002 s, total=0.021 s; sync files=2, longest=0.001 s, average=0.001 s; distance=0 kB, estimate=0 kB
2026-03-04 09:16:23.940 UTC [42] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-04 09:16:24.041 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 09:16:24.041 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 09:16:24.041 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 09:16:24.049 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 09:16:24.062 UTC [56] LOG:  database system was shut down at 2026-03-04 09:16:23 UTC
2026-03-04 09:16:24.075 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 09:21:51.439 UTC [54] LOG:  checkpoint starting: time
2026-03-04 09:21:54.494 UTC [54] LOG:  checkpoint complete: wrote 33 buffers (0.2%); 0 WAL file(s) added, 0 removed, 0 recycled; write=3.027 s, sync=0.009 s, total=3.056 s; sync files=10, longest=0.004 s, average=0.001 s; distance=151 kB, estimate=151 kB
2026-03-04 09:32:37.682 UTC [1] LOG:  received fast shutdown request
2026-03-04 09:32:37.868 UTC [1] LOG:  aborting any active transactions
2026-03-04 09:32:37.874 UTC [1] LOG:  background worker "logical replication launcher" (PID 59) exited with exit code 1
2026-03-04 09:32:37.874 UTC [54] LOG:  shutting down
2026-03-04 09:32:37.991 UTC [54] LOG:  checkpoint starting: shutdown immediate
2026-03-04 09:32:38.792 UTC [54] LOG:  checkpoint complete: wrote 0 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.001 s, sync=0.001 s, total=0.919 s; sync files=0, longest=0.000 s, average=0.000 s; distance=0 kB, estimate=136 kB
2026-03-04 09:32:38.807 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 09:33:10.430 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 09:33:10.431 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 09:33:10.431 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 09:33:10.447 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 09:33:10.465 UTC [29] LOG:  database system was shut down at 2026-03-04 09:32:38 UTC
2026-03-04 09:33:10.487 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 09:38:37.831 UTC [27] LOG:  checkpoint starting: time
2026-03-04 09:38:37.856 UTC [27] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.008 s, sync=0.003 s, total=0.026 s; sync files=2, longest=0.002 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-04 09:39:59.525 UTC [1] LOG:  received fast shutdown request
2026-03-04 09:39:59.530 UTC [1] LOG:  aborting any active transactions
2026-03-04 09:39:59.537 UTC [1] LOG:  background worker "logical replication launcher" (PID 32) exited with exit code 1
2026-03-04 09:39:59.540 UTC [27] LOG:  shutting down
2026-03-04 09:39:59.544 UTC [27] LOG:  checkpoint starting: shutdown immediate
2026-03-04 09:39:59.556 UTC [27] LOG:  checkpoint complete: wrote 0 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.001 s, sync=0.001 s, total=0.016 s; sync files=0, longest=0.000 s, average=0.000 s; distance=0 kB, estimate=0 kB
2026-03-04 09:39:59.566 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 09:41:39.855 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 09:41:39.856 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 09:41:39.856 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 09:41:39.868 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 09:41:39.879 UTC [30] LOG:  database system was shut down at 2026-03-04 09:39:59 UTC
2026-03-04 09:41:39.906 UTC [1] LOG:  database system is ready to accept connections
2026-03-04 09:43:15.008 UTC [1] LOG:  received fast shutdown request
2026-03-04 09:43:15.017 UTC [1] LOG:  aborting any active transactions
2026-03-04 09:43:15.023 UTC [1] LOG:  background worker "logical replication launcher" (PID 33) exited with exit code 1
2026-03-04 09:43:15.027 UTC [28] LOG:  shutting down
2026-03-04 09:43:15.029 UTC [28] LOG:  checkpoint starting: shutdown immediate
2026-03-04 09:43:15.045 UTC [28] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.004 s, sync=0.003 s, total=0.018 s; sync files=2, longest=0.002 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-04 09:43:15.055 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-04 09:43:48.552 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-04 09:43:48.553 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-04 09:43:48.553 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-04 09:43:48.560 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-04 09:43:48.577 UTC [28] LOG:  database system was shut down at 2026-03-04 09:43:15 UTC
2026-03-04 09:43:48.598 UTC [1] LOG:  database system is ready to accept connections


## Issues Encountered

None.