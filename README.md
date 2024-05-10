
# MongoDB Installation using Docker

This guide outlines the steps to set up and run a MongoDB instance using Docker, with customized configuration and remote access.

## Prerequisites

Make sure you have Docker installed on your machine. You can find installation instructions for different operating systems [here](https://docs.docker.com/get-docker/).

## Installation Steps

Execute the following command in the terminal:

```bash
docker run -d -p 80:27017 --name mongo -v $(pwd)/mongod.conf:/etc/mongod.conf -e MONGODB_INITDB_ROOT_USERNAME=admin -e MONGODB_INITDB_ROOT_PASSWORD=password mongodb/mongodb-community-server:latest
```

This command creates and starts a Docker container with the following configurations:

- Port 27017 of the container is mapped to port 27017 of the host.
- The local `mongod.conf` configuration file is mounted inside the container at `/etc/mongod.conf`.
- Sets the database username as `admin` and password as `password`.
- Utilizes the latest MongoDB Community Server image available on Docker Hub.

## Remote Access

After the container is running, you can access MongoDB remotely using a database client such as MongoDB Compass or through the command line.

To connect to the MongoDB server, use the following connection URI:

```
mongodb://admin:password@<SERVER_IP>:27017
```

Replace `<SERVER_IP>` with the IP address or hostname of the server where the Docker container is being executed.

## Notes

- Make sure to modify the password and other parameters according to your security needs.
- For more information on MongoDB configuration, refer to the official documentation at [docs.mongodb.com](https://docs.mongodb.com/manual/).
```
