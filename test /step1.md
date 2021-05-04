# Let's create some basic files that we will use in our program

In order to get Docker to run a specific application, we need to create a few. This includes the Dockerfile and any other files that would be necessary for the application to work. In this instance, we will be creating the two python files: wsgi.py and app.py, and we will create our Dockerfile. To make this process go by quicker, we provided the information needed for each file. Instead of giving you the files themselves, this will give you practice learning how to create files and work inside the editor that is provided at the top of the terminal.

### Let's start with the wsgi.py file

To create the file, run the following command in the terminal:

`touch wsgi.py`{{execute}}

Next, you will go to the editor and click on the newly created wsgi.py file to open it.

Now, we have to copy the following lines into the wgsi.py file. Each of the lines are on a separate line.

`from app import app`{{copy}}

`if __name__ == "__main__":`{{copy}}

*In case the editor has not done this automatically, this line should be about 4 spaces indented*
`    app.run()`{{copy}}


### Next, let's create the app.py file

To create the file, run the following command in the terminal:

`touch app.py`{{execute}}

Next, you will go to the editor and click on the newly created app.py file to open it.

Now, we have to copy the following lines into the app.py file. Each of the lines are on a separate line.

`from flask import Flask`{{copy}}

`import socket`{{copy}}

`app = Flask(__name__)`{{copy}}

`@app.route("/")`{{copy}}

`def hello():`{{copy}}

*In case the editor has not done this automatically, this line should be about 4 spaces indented*
`    return "<h1 style='color:blue'>Hello There from {}!</h1>".format(socket.gethostname())`{{copy}}

*This line should NOT be indented. If the editor made the indent, please remove it*
`if __name__ == "__main__":`{{copy}}

*In case the editor has not done this automatically, this line should be about 4 spaces indented*
`    app.run(host ='0.0.0.0')`{{copy}}


### Finally, we can create the Dockerfile

To create the file, run the following command in the terminal:

`touch Dockerfile`{{execute}}

Next, you will go to the editor and click on the newly created Dockerfile to open it.

Now, we have to copy the following lines into the Dockerfile. Each of the lines are on a separate line.

`FROM python:3.8-slim-buster`{{copy}}

`WORKDIR /app`{{copy}}

`RUN python3 -m venv /.venv`{{copy}}

`RUN /.venv/bin/pip install flask gunicorn`{{copy}}

`COPY wsgi.py .`{{copy}}

`COPY app.py .`{{copy}}

`CMD ["/.venv/bin/gunicorn", "--bind", "0.0.0.0:5000", "wsgi:app"]`{{copy}}

Once all of these lines are copied over, you may move onto the next step.
