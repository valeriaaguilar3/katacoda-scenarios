## Learning More Docker Commands

### Docker Daemon 

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


### Creating The Docker Compose File 

Now you will create the docker compose file: 

`touch docker-compose.yml`{{execute}}

Copy the following lines into the file: 

`version: "2.2"`{{copy}}

Hit enter to move to the next line. 

Copy the next line and paste it directly under the first line. 

`services: `{{copy}}

Hit enter to move to the next line. 

Before pasting this line, you should indent by hitting the space bar 4 times. 

`    flask_app: `{{copy}}

Then hit enter to move to the next line. 

Before pasting this line, make sure the cursor is directly underneath 'flask_app: ' and hit the space bar 2 times to indent. 

`      build: .`{{copy}}


This file defines the services that are being used.

After completeing docker-compose.yml file, try this command: 

`docker-compose up -d`{{execute}}

You now have a running container! 

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

### Stopping And Removing The Container With Docker Compose 

To stop and remove the container, execute the command below: 

`docker-compose down`{{execute}}

You have now seen the basics of Docker Compose! 