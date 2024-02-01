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
