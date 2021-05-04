## Learning More Docker Commands

### Docker Detach

Now we will restart the container with the command: 
`docker run -d app`{{execute}}

Using '-d' in the command line will allow you to run a docker container in the background so you can continue to use your terminal. 

### Docker PS

Lets talk about a very helpful command in Docker. Try the command: 

`docker ps`{{execute}} 

This command will prompt you with quite a bit of information. The information includes:
* The CONTAINER ID
* The IMAGE name 
* The COMMAND that was used to create the container
* When the container was CREATED
* The STATUS which tell us how long the container has been running
* The PORTS the container is running on
* The NAME of the container

Copy the command below into the terminal, but do not execute just yet: 

`docker stop <CONTAINER ID>`{{copy}}

Now, copy the CONTAINER ID and replace ' <CONTAINER ID> ' with the actual ID that you just copied and hit execute.
This command will stop the running container. 

Copy the command below into the terminal, but do not execute just yet: 

`docker rm <CONTAINER ID>`{{copy}}

This command will will remove the container. 


### Creating the NGINX.CONF file

Create the nginx file: 

`touch nginx.conf`{{execute}}

<pre class="file" data-target="clipboard">
events {
}

http{
    server {
        listen 80 default_server;
        server_name _;

        location /app {
            proxy_pass http://flask_app:5000/;
        }
    }
}
</pre>


### Creating The Docker Compose File 

Now you will create the docker compose file: 

`touch docker-compose.yml`{{execute}}

Copy the the file below into the docker-compose.yml file:

<pre class="file" data-target="clipboard">
version: "3.9"
services:
    flask_app:
      build: . 
    nginx:
      image: nginx
      volumes:
        - ./nginx.conf:/etc/nginx/nginx.conf
      ports: 
        - "3000:80"
</pre>

This file defines the services that make up your app in docker-compose.yml so they can be run together in an isolated environment.

After completeing docker-compose.yml file, try this command: 

`docker-compose up -d`{{execute}}

You now have a running container with an Nginx image!

You can double check that your app is up and running with the command: 

`docker-compose logs`{{execute}}

And also with: 

`docker-compose ps`{{execute}}


### Stopping And Removing Docker Compose 

To stop and remove the container, execute the command below: 

`docker-compose down`{{execute}}

You have now seen the basics of Docker Compose! 