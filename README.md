[Ondrej Sika (sika.io)](https://sika.io) | <ondrej@sika.io>

# Graylog Training

## Course

## Install using Docker Compose

```
git clone https://github.com/Graylog2/docker-compose graylog
```

```
cd graylog/open-core
```

Create `.env` file with following content:

```
echo GRAYLOG_PASSWORD_SECRET=aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa >> .env
echo GRAYLOG_ROOT_PASSWORD_SHA2=ca978112ca1bbdcafac231b39a23dc4da786eff8147c4e72b9807785afee48bb >> .env
```

Increase `max_map_count` for OpenSearch:

```
sysctl -w vm.max_map_count=262144
```

```
docker-compose up -d
```

That's it. Graylog is running on http://graylog.sikademo.com:9000

See `docker compose logs` for initial password.

## Syslog TCP Input

- [Docs: Getting in Logs](https://go2docs.graylog.org/5-2/getting_in_log_data/getting_in_log_data.html)
- [Docs: Ingest Syslog](https://go2docs.graylog.org/5-0/getting_in_log_data/ingest_syslog.html)

Create Syslog TCP Input on port `5140` (System > Inputs > Select Input > Syslog TCP).

http://graylog.sikademo.com:9000/system/inputs

![graylog-syslog-tcp-input](images/graylog-syslog-tcp-input.png)

Install `rsyslogd`

```
apt install rsyslog
```

Create file `/etc/rsyslog.d/10-graylog.conf` with following content:

```
*.* @@graylog.sikademo.com:5140;RSYSLOG_SyslogProtocol23Format
```

Restart `rsyslogd`

```
systemctl restart rsyslog
```

See the logs in Graylog
