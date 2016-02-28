# Elasticsearch, Logstash, Kibana with Curator and Beats support
**Ready to go Docker configuration for set up ELK stack in a minutes**

## Description
- [Elasticsearch](https://hub.docker.com/_/elasticsearch/) - official image with data volume in `elasticsearch/data` directory
- [Logstash](https://hub.docker.com/_/logstash/) - official image + custom configuration which takes care about Filebeat, Topbeat and Packetbeat index templates for Elasticsearch + multiline option for correct stacktraces representation
- [Kibana](https://hub.docker.com/_/kibana/) - official image
- [Curator](https://github.com/elastic/curator) - lightweight 50mb container which could run scheduled tasks against Elasticsearch to manage its indices (delete, optimize, snapshot, etc)

![scheme](https://cloud.githubusercontent.com/assets/6069066/13380670/550082e0-de59-11e5-98ff-a4b7a30ae719.png)

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
docker-compose logs curator
```

## Scaling up
This simple configuration will run very happily on your laptop, but it can be easely scaled up for highload production servers with a huge amount of logs and monitoring data.

- Learn about [Elasticsearch cluster and horizontal scaling](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html)
- Consider [Logstash scaling](https://www.elastic.co/guide/en/logstash/current/deploying-and-scaling.html) with multiple shipping and indexing instances with MQ in the middle

## Notes
- You may want to add [Kibana Shield plugin](https://www.elastic.co/guide/en/shield/current/kibana.html) for users authentication
- It might be really helpful to use [Elasticsearch Watcher](https://www.elastic.co/products/watcher) or [Yelp ElastAlert](https://github.com/Yelp/elastalert) to get notified on significant events or anomalies in your data
- You can specify resource limits (like CPU and memory allocation) for each docker container

Feel free to contact me with any issues and questions
