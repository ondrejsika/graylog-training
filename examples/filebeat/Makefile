stdin-loggen:
	slu loggen | filebeat -e -c $(shell pwd)/filebeat-stdin.yml

docker:
	filebeat -e -c $(shell pwd)/filebeat-docker.yml
