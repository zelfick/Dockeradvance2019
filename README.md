# advancedockerchallenge
# Assignment: Create A Multi-Service Multi-Node Web App

## Goal: create networks, volumes, and services for a web-based "cats vs. dogs" voting app.
Here is a basic diagram of how the 5 services will work:

![diagram](./challenge2/architecture2.png)
- All images are on Docker Hub, so you should use editor to craft your commands locally, then paste them into swarm shell (at least that's how I'd do it)
- a `backend` and `frontend` overlay network are needed. Nothing different about them other then that backend will help protect database from nodejs app.
- The database server should use a named volume for preserving data. Use the new `--mount` format to do this: `--mount type=volume,source=db-data,target=/var/lib/postgresql/data`

# create two overlay networks one for frontend and the other for backend
docker network create --driver overlay frontend
docker network create --driver overlay backend

# create the service NodeJS con React, with 3 replicas, connect it with the  correspondent network and use a standard port 80, 
# give a name in accordance with the project you are working on (Tournaments or parking) 


# create the service javaspring, with 2 replicas, connect it with the  correspondent network and use the port 8181, 
# give a name in accordance with the project you are working on (Tournaments or parking)


#create a service for database
#create service db: postgres:9.4, one named volume pointing to /var/lib/postgresql/data, backend, 1 replica
#to mount the volume use the option: --mount type=volume,source=db-data,target=/var/lib/postgresql/data
docker service create --name db --replicas 1 --network backend --mount type=volume,source=db-data,target=/var/lib/postgresql/data -e POSTGRES_PASSWORD=password postgres:9.4

#bonus
#configure a visualizer for the services

#To start with the project do it like this:
First create the four components and run in your machine and inspect their logs to see the components are running correctly
Write a compose file that brings up all the solution
Create the nodes using docker-machine (you can use the scripts in the repository)
create the swarm and using service commands bring up the redundancy solutions
