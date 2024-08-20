# Products Store Backend
This Launcher creates a container that runs various services to run Application Backend.

It runs following services:

- nats-server: Nats its an application that exchanges messages (it means data between services)
- client-gateway: Proccess al request and send them to their respective services through Nats Server
- products-store-db: Server with a Postgres Database for our application
- products-store-ms: Microservice with services related to our application (this service depends on 'products-store-db' service)
- payments-ms: Microservice with services related to Payments Sessions (in this case we used Stripe to proccess payment data)

## Development Launcher

1. Clone Project Repository
2. Create a **.env** file based on **.env.template** file
3. Run command: `git submodule update --init --recursive` to build submodule folders
4. Run command: `docker compose up --build`

## Production Launcher
