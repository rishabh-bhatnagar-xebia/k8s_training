Task 1: Build & push java web-server docker image to docker hub

**Requirements:**

1.  Need to create a Dockerfile for building the java web-server
    application.

2.  Name of the docker image on docker hub should be
    **"java-web-server"**

3.  The docker image on docker hub should have 2 tags **"latest" &
    "0.1.0"**

**Material:**

1.  Application source code can be found at
    [github](https://github.com/xi3161-sregoti/java-web-server)

    a.  Read the readme.md file on how to run the application

**Expected Result:**

1.  Dockerfile should be pushed in your forked repository

2.  Update the readme.md with link of your docker hub registry where the
    image exists

**Tips:**

1.  First try to run the app locally:

    a.  Fork the specified github repository, clone the repository & run
        the app locally using the command specified in the repository.
        Interact with the app\...

2.  Before pushing to docker hub, create a container test the app
    functionality is working as intended (Opening it in browser, should
    show red screen) .

Task 2: Write a docker-compose file for a java web-server app

**Requirements:**

1.  The compose file should run 2 containers.

    a.  App (java web-server) container

    b.  Database (postgres) container

2.  App container specifications:

    a.  Docker Image Name: Use the image created in task 1

    b.  Docker Image Tag: **0.1.0**

    c.  Expose on port **8080**

    d.  Set the following environment variable to specify the postgres
        > database connection string. The application uses this value to
        > connect to the database

        i.  **CONN="
            jdbc:postgresql://localhost:5432/postgres?user=postgres&password=
            test-db-password"**

3.  Database container specifications:

    a.  Docker Image Name: **"postgres"**

    b.  Docker Image Tag: **"15.1-alpine"**

    c.  Use and environment variable to change the postgres password
        **"test-db-password"**

    d.  The Postgres database stores critical information about our
        application. So, we don't want the data to get wiped out when
        the container is removed.\
        That's why we use a volume mount to store data on the host
        system.

        i.  Default Directory of host where we want to store container
            data will be:\
            **"/java-web-app/docker/data"**

        ii. Default Directory of postgres where it stores data in
            container:\
            **"/var/lib/postgresql/data"**

    e.  The database container should start before the app container.

**Expected Result:**

1.  Docker compose file should be pushed in your forked repository

2.  When "docker-compose" up command is run. We should be access the
    application on localhost:8080 & the application should be in green
    state

**Tips:**

1.  Read the postgres documentation at
    > [github](https://github.com/docker-library/docs/blob/master/postgres/README.md)

    a.  [Usage
        Instructions](https://github.com/docker-library/docs/blob/master/postgres/README.md#how-to-use-this-image)

    b.  [Handling
        > PGDATA](https://github.com/docker-library/docs/blob/master/postgres/README.md#pgdata)
