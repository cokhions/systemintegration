# systemintegration
Docker project
run all containers to verify installation:
`docker-compose up`

### NOTES
- docker-compose 2.1 used to be able to wait for rabbit spin up (more in the file)
- it can take about a minute (after all images are downloaded) to spin up rabbit - there is a healthcheck waiting for rabbit to listen on it's 5672
- i did not implemented postgress healthcheck as I do not what containers depends on it, also postgress is starting faster than rabbit
- alpine linux images are used for smaller images to be downloaded
- rabbit management available on http://localhost:15672 (guest/guest login)
- inter container connectivity is available via docker container names as hostnames
- python and node scripts are just for example to demonstrate working connectivity
- node dependencies for both `backend` and `frontend` are auto fetched only if there is no node_modules in corresponding project - for dependencies to be updated you need either run npm i inside the container or remove the `node_modules` to force re-installing them
- python scripts require currently only one dependency which is installed each time `consumer`/`publisher` container is started - alternative would be to create a simple `Dockerfile` installing deps from `requirements.txt` on top of `python` image
