# Test Cube integration with Superset

Docker Cube image - https://hub.docker.com/r/cubejs/cube
Docker Superset image - https://hub.docker.com/r/apache/superset


```bash
docker pull cubejs/cube:latest
docker run -d -p 3000:3000 -p 4000:4000 \
  -e CUBEJS_DB_HOST=postgres://hostname \
  -e CUBEJS_DB_NAME=<DB_NAME> \
  -e CUBEJS_DB_USER=<USER> \
  -e CUBEJS_DB_PASS=<PASS> \
  -e CUBEJS_DB_TYPE=<DB_TYPE> \
  -e CUBEJS_API_SECRET=<API_SECRET> \
  -v $(pwd):/cube/conf \
  cubejs/cube:latest
```


## After run superset:

```bash
docker exec -it superset superset fab create-admin \
              --username admin \
              --firstname Superset \
              --lastname Admin \
              --email admin@superset.com \
              --password admin

```

Migrate local DB to latest:    

``$ docker exec -it superset superset db upgrade``

Load Examples:   

``$ docker exec -it superset superset load_examples``

Setup roles:     

``$ docker exec -it superset superset init``

Login and take a look -- navigate to http://localhost:8080/login/ -- u/p: [admin/admin]


# Web UI

- Cube web - localhost:4000
- Superset web - localhost:8080


# Integration Cube with Postgres data warehouse 

