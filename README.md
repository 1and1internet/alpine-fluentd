# Fluentd docker image

This container image is to create endpoint to collect logs on your host.

Default configurations are to:

* listen port `24224` for Fluentd forward protocol
* store logs with tag `docker.**` into `/fluentd/log/docker.*.log` (and symlink `docker.log`)
* store all other logs into `/fluentd/log/data.*.log` (and symlink data.log)

## Configurable ENV variables

Environment variable below are configurable to control how to execute fluentd process:

### FLUENTD_CONF

It's for configuration file name, specified for `-c`.

If you want to use your own configuration file (without any optional plugins), you can use it over this ENV variable and -v option.

1. write configuration file with filename `yours.conf`
2. execute `docker run` with `-v /path/to/dir:/fluentd/etc` to share `/path/to/dir/yours.conf` in container, and `-e FLUENTD_CONF=yours.conf` to read it

### FLUENTD_OPT

Use this variable to specify other options, like `-v` or `-q`.

### References

[Docker Logging | fluentd.org](http://www.fluentd.org/guides/recipes/docker-logging)

[Fluentd logging driver - Docker Docs](https://docs.docker.com/engine/reference/logging/fluentd/)
