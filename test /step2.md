## Logging into your Docker Account in the Terminal

As mentioned in the intro, a Docker Desktop account is needed in order to make a docker container. Otherwise, you will get a *too many requests* error and will not be able to see the outputs of the following commands. If you need to create an account, go to this website <https://hub.docker.com> and sign up for free. If you already have an account or have just created it, please run the command and then provide your username and password:

`docker login`{{execute}} 


## Building and Running Containers

Once you've configured your Dockerfile how you want and have logged onto your docker account, you can now build your very first Docker container. This is done by using the 'docker build' command. When you are ready, type the command below to start the build process
or click on it to execute the command for you.

### The Docker Build Command

`docker build -t app .`{{execute}}

We gave the command above an argument to give our container a name. Passing the
'-t' argument and then a name for your container, then builds the image using
the name you passed. The same process can be done by using the '--tag' option as
well. Although, the name of your image must contain all lowercase letters and no
spaces or the command will not execute. The period at the very end of the
command tells Docker where to look for the Dockerfile. If you do not pass this
argument, Docker will look in your current present working directory by default.

### Running Your First Container

Your image called 'app' is now built and ready to execute. To start your app
image, execute the line below.

`docker run app`{{execute}}

This command will start your Docker container and since you passed the argument
'app' it will look for the app image and use that Dockerfile to run your
container. If you do not originally name your image, one will be created for you
and you can use that as well.
