# Products Store Backend
This Launcher creates a container that runs various services to run Application Backend.
All services were mounted in Docker Containers.

#### It runs following services:

- nats-server: Nats its an application that exchanges messages (it means data between services)
- client-gateway: Proccess al request and send them to their respective services through Nats Server
- products-store-db: Server with a Postgres Database for our application
- products-store-ms: Microservice with services related to our application (this service depends on 'products-store-db' service)
- payments-ms: Microservice with services related to Payments Sessions (in this case we used Stripe to proccess payment data)

#### Project Process Diagram

<p align="center">
  <a href="https://github.com/MrDanii/products-store-launcher" target="blank"><img src="https://res.cloudinary.com/dbrepifea/image/upload/v1730061214/products-store-process-diagram-transparent_ewkriv.png" width="100%" alt="Nest Logo" /></a>
</p>

## Development Launcher

1. Clone Project Repository
2. Create a **.env** file based on **.env.template** file
3. Run command: `git submodule update --init --recursive` to build submodule folders
4. Run command: `docker compose up --build`

__*Note*__: when you execute `docker compose up --build` a folder "postgres-data" is created inside git submodule "products-store-ms" (this mantains database configuration and data)
In case you need to change database configuration, don't forget to delete that folder to force the container to change Database server to take
the new configuration. 

## Production Launcher

1. Clone Project Repository
2. Change branch to (cloud-build) branch
3. Run command: `docker compose -f docker-compose.prod.yml --env-file .env.prod up --build` to run production version of docker compose. 

__*Note*__: if your didn't create ".env.prod" file only run `docker compose -f docker-compose.prod.yml up --build`

#### Quick View on prisma schema and Entity Relation Diagram

- Database was made with prisma, you can see table definition on __schema.prisma__ file on products-store-ms git submodule.
to change table or fields it's necesarry generate respective migration.
- You can see more info on the "README.md" inside git submodule "products-store-ms"

<p align="center">
  <a href="https://github.com/MrDanii/products-store-launcher" target="blank"><img src="https://res.cloudinary.com/dbrepifea/image/upload/v1730060660/er-database_ijmgni.png" width="100%" alt="Nest Logo" /></a>
</p>

- __Note__: This diagram was generated with ([Software Ideas Modeler](https://www.softwareideas.net/en/download))
- *Since this app project was made with learning purposes, __Software__ Ideas Modeler can be used without violating the non-commercial-use clause