# Cassandra

## TODO

- [ ] Include a web UI alongside Cassandra

## Usage

- Currently this does not contain a web UI (as per other compose setups). There are a few to investigate and try to get working (some sources listed below)
  - https://github.com/orzhaha/cassandra-web
  - https://github.com/avalanche123/cassandra-web
  - https://hub.docker.com/r/ipushc/cassandra-web
  - https://hub.docker.com/r/dcagatay/cassandra-web

### Settings

- `master password` is disabled

## Sources

- https://medium.com/@Shamimw/running-apache-cassandra-locally-with-docker-step-by-step-guide-with-cql-python-c9e8ab3212b7
- https://medium.com/@saurabhg.engineer/how-to-run-cassandra-including-web-interface-locally-in-two-simple-steps-6c9449defb97
- https://github.com/dogukancagatay/docker-cassandra-web/blob/master/docker-compose.yml

## Notes

Work in progress running `cassandra-web`

```cmd
docker run -d -p 9042:9042 --name cassandra cassandra:latest

docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' cassandra


docker run -d -e CASSANDRA_HOST_IP=$(docker inspect --format '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' cassandra) -e CASSANDRA_PORT=9042 -p 3000:3000 --name cassandra-web delermando/docker-cassandra-web:v0.4.0
docker run -d -e CASSANDRA_HOST_IP=localhost -e CASSANDRA_PORT=9042 -p 3000:3000 --name cassandra-web delermando/docker-cassandra-web:v0.4.0



docker run -d -e CASSANDRA_HOST_IP=172.21.0.2 -e CASSANDRA_PORT=9042 -p 3000:3000 --name cassandra-web ipushc/cassandra-web



docker run -d -e CASSANDRA_HOST_IP=172.21.0.2 -e CASSANDRA_PORT=9042 -p 3000:3000 --name cassandra-web2 delermando/docker-cassandra-web:v0.4.0
```
