# Elasticsearch, Logstash, Kibana with Curator and Beats support
**Ready to go Docker configuration for set up ELK stack in a minutes**

## Description

- [Elasticsearch](https://hub.docker.com/_/elasticsearch/) - official image with data volume in `elasticsearch/data` directory
- [Logstash](https://hub.docker.com/_/logstash/) - official image + custom configuration, which takes care about Filebeat, Topbeat and PacketBeat index templates for Elasticsearch + multiline option for stacktraces correct representation
- [Kibana](https://hub.docker.com/_/kibana/) - official image
- [Curator](https://github.com/elastic/curator) - lightweight 50mb container which could run scheduled tasks against Elasticsearch to manage its indices (delete, optimize, snapshot, etc)

## Setup
1. Install required Beats shippers on the host which should be monitored
2. Install Docker and Docker Compose on the ELK host
3. Clone this repository and hit `docker-compose build`

## Usage
Start everything with one command:
```
docker-compose up -d
```

Keep track of your containers execution. For example, controll Curator scheduled tasks:
```
docker-compose logs | grep curator
```

## Notes
- You may want to add nginx container with configs HTTP Basic Auth for Kibana
- You can specify resource limits (like CPU and memory allocation) for each docker container
- Feel free to contact me with any questions and issues
