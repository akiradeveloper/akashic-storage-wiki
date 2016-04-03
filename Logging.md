akashic-storage utilizes logback library to leave logs for debugging.

All logs are stored in `/opt/akashic-storage/log` directory and
very helpful for debugging.
So when you send me a bug report and not sure the real cause is
please send all the logs under the directory.

The following is the list of logs:

* daemon.log: Stdout from apache-daemon
* daemon_error.log: Stderr from apache-daemon
* admin.log: All logs relevant to user accounting.
* error.log: All errors from logback
* all.log: All logs from logback (can be suppressed by editing logback.xml)

The config (`/opt/akashic-storage/etc/logback.xml`) is editable but not recommended. The default setting remains all logs below DEBUG level but the amount of logs are trivial and not hurts the performance.

