Packaging InfluxDB for Debian/Ubuntu
===

Packaging Influx in a nutshell

* Build Influx
* Build Admin Site
* Create structure
* Update Configs
* FPM Package

Building InfluxDB
---

https://github.com/influxdb/influxdb/blob/master/docs/contributing.md


Building InfluxDB-Admin
---

https://github.com/influxdb/influxdb-admin/blob/master/README.md


Creating Structure
---

See this repo's structure


Tweak Configs
---

See diffs from this repo's config files vs InfluxDB upstreams (mostly file paths, but also upstart vs initd, and a different postinstall)


FPM Package
---

Use FPM: https://github.com/jordansissel/fpm

```
fpm --vendor InfluxDB \
    --license mit \
    --maintainer '<bmhatfield@gmail.com>' \
    --url 'http://influxdb.com/' \
    --description 'An open-source distributed time series database with no external dependencies' \
    -s dir \
    -t deb \
    -n influxdb \
    -v 0.8.0-rc4 \
    --after-install after-install \
    --config-files etc/influxdb/benchmark_config.toml \
    --config-files etc/influxdb/config.toml \
    --config-files etc/init/influxdb.conf \
    etc usr
```
