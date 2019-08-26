# advancedockerchallenge
# Assignment: Create A Multi-Service Multi-Node Web App

## Goal: create networks, volumes, and services for a web-based "nodejs spring postgress + visualizer" app.
Here is a basic diagram of how the 4 services will work:

![diagram](./challenge2/architecture2.png)
- You have to build all the images, but must of them you already have it, so you should use editor to craft your commands locally, then paste them into swarm shell (at least that's how I'd do it)
- a `backend` and `frontend` overlay network are needed. Nothing different about them other then that backend will help protect database from external world.
- The database server should use a named volume for preserving data. Use the new `--mount` format to do this: `--mount type=volume,source=db-project_name,target=/var/lib/postgresql/data`

# create two overlay networks one for frontend and the other for backend
docker network create --driver overlay frontend
docker network create --driver overlay backend

# create the service NodeJS con React, with 3 replicas, connect it with the  correspondent network and use a standard port 80, 
# give a name in accordance with the project you are working on (Tournaments or parking) 


# create the service javaspring, with 2 replicas, connect it with the  correspondent network and use the port 8181, 
# give a name in accordance with the project you are working on (Tournaments or parking)


# create a service for database db: postgres:9.4, one named volume pointing to /var/lib/postgresql/data, backend, 1 replica
#to mount the volume use the option: --mount type=volume,source=db-data,target=/var/lib/postgresql/data


# configure a visualizer for the services

#To start with the project do it like this:
First create the four components and run in your machine and inspect their logs to see the components are running correctly
Write a compose file that brings up all the solution
Create the nodes using docker-machine (you can use the scripts in the repository)
create the swarm and using service commands bring up the redundancy solutions
