# Start a multi-node cluster with Docker Compose

[refer link](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)

## Set vm.max_map_count to at least 262144

##### Windows with Docker Desktop WSL 2 backend

The vm.max_map_count setting must be set in the docker-desktop container:

```
wsl -d docker-desktop
sysctl -w vm.max_map_count=262144
```

## Start your cluster with security enabled and configured

1. Modify the .env file and enter strong password values for both the ELASTIC_PASSWORD and KIBANA_PASSWORD variables.

2. Create and start the three-node Elasticsearch cluster and Kibana instance:

```
docker-compose up -d
```

3. When the deployment has started, open a browser and navigate to http://localhost:5601 to access Kibana, where you can load sample data and interact with your cluster.

```
username: elastic
password: Test@123 (the one set in .env file)
```

https://localhost:9200/

```
username: elastic
password: Test@123 (the one set in .env file)
```

## Stop and remove the deployment

To stop the cluster, run docker-compose down. The data in the Docker volumes is preserved and loaded when you restart the cluster with docker-compose up.

```

docker-compose down

```

To delete the network, containers, and volumes when you stop the cluster, specify the -v option:

```

docker-compose down -v

```

```

```
