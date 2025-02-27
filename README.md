# Run Lizmap stack with docker-compose

Run a complete Lizmap stack with test data. 

- Lizmap Web Client
- QGIS Server
- Redis
- PostGIS
- Cloud Commander

**Note**: this is a sample configuration for testing Lizmap web client with QGIS and WPS features: 
if you want use it on a production server you will need to make adjustments for meeting 
your production requirements. 

## Requirements

- Docker engine
- docker-compose
- make (optional in Windows)

## Quick start

Execute those commands above for your system and open your browser at http://localhost:8090.

### Linux

In command shell execute to test last version:
```
make start
```
Or if you want to test specific version (here last 3.3.x version):
```
make start LIZMAP_VERSION_TAG=3.3
```

### Windows

You can execute same commands as Linux part given above if you use `make` (optional).

Or in command powershell execute:

```
docker-compose --env-file .env.windows up
```
Or if you want to test specific version, you can edit `.env.windows` and change (here last 3.3.x version):

```
LIZMAP_VERSION_TAG=3.3
```

## Running the first time

The command creates a docker-compose environnement and start the stack.

The Lizmap service will start two toys projects that you will have to configure in the Lizmap
interface.

See the [Lizmap documentation](https://docs.lizmap.com) for how to configure Lizmap at first run.

Default login is `admin`, password `admin`. It will be asked to change it at first login.

## Add your own project

You need to :
* create a directory in `lizmap/instances`
* visit http://localhost:8090/admin.php/admin/maps/
* in the Lizmap admin panel, add the directory you created
* add one or more QGIS projects with the Lizmap CFG file in the directory

## Upload your own project online

* set your login user and password for cloud commander in `Makefile`
* visit http://localhost:8090/cloudcmd/
* upload your own project directory to the server

## Reset the configuration

In command line

```
make clean 
```

This will remove all previous configuration. You will have to reenter the configuration in Lizmap
as for the first run.

For more information, refer to the [docker-compose documentation](https://docs.docker.com/compose/)

Refs:
    - https://github.com/3liz/lizmap-web-client
    - https://github.com/3liz/py-qgis-server
