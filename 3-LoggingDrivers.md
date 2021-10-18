# Logging Drivers

pluggable framerowk for accessing log data from services and container in docker.

To configure the default behaviour for `log-driver` and `log-otps` we can modify the `/etc/docker/daemon.json`.

To see the supported logging drivers : https://docs.docker.com/config/containers/logging/configure/

To change the logging driver at the container level use the `--log-driver` and `--log-opt` flag when using `docker run` command.