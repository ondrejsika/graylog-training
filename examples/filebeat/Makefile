stdin-loggen:
	slu loggen | filebeat -e -c $(shell pwd)/filebeat-stdin.yml

stdin-json:
	slu loggen --log-prefix loggen-stdin-json --json | filebeat -e -c $(shell pwd)/filebeat-stdin-json.yml

docker:
	filebeat -e -c $(shell pwd)/filebeat-docker.yml
