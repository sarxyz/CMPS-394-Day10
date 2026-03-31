# CMPS-394-Day 7

## Lab 1: Fitting the Pieces Together
You have been supplied a basic ui served via nginx, a hello world Go API, and a PostgreSQL 16 database. Your task is to finish the docker compose file to get all three services running together. The UI should be able to call the API, and the API should be able to connect to the database.
- The UI should be available on port 80 of the host machine.
- The API should be available on port 8080 of the host machine.
    - You will need to define these environment variables for the API to connect to the database:
        - DB_HOST
        - DB_PORT
        - DB_USER
        - DB_PASSWORD
        - DB_NAME
    - Note: The API will be making requests to the database from inside of docker, so take that into account when setting the DB_HOST variable.
- The API should wait on the database to be healthy before starting up.
    - look up the depends_on option in docker compose and how to use it with a healthcheck
- You'll know you have everything set up correctly when the UI shows "Hello, World!" in blue text in the center of the screen.

## Lab 2: Docker Compose Networking
Modify the docker compose file from Lab 1 to use a custom network. This will allow the services to communicate with each other using their service names as hostnames.
- Create a custom network called "app_network" in the docker compose file
- Connect all three services (db, api, ui) to the "app_network" network
- Update the DB_HOST environment variable for the API service to use the service name of the database
- Comment out the port mapping for the database service, as it will no longer be needed for the API to connect to it
- Verify that the UI still shows "Hello, World!" in blue text in the center of the screen
    - You will most likely need to recreate the containers for the changes to take effect, use `docker compose down` and `docker compose up --build` to do so.

## Assignment: Python API in a Compose Network
Take the Python API and database you created in the previous class's assignment and wire it up to a basic UI served via nginx using docker compose like we did in the labs today. You should use a custom network and the database should not be exposed to the host machine.
- It is up to you if you want to use a JS framework or just a simple HTML page for the UI
- Your API should use environment variables to get the database connection information, and it should wait on the database to be healthy before starting up
- You do not need to add support for every endpoint you created. Just a GET endpoint will do.
Links to an external site.

Piep waz hear! 
