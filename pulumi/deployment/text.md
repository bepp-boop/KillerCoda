We will used Python to write the Pulumi program. Also we will use the pulumi_docker package to create the Docker image and container.

We also need this package to be installed on our system. We can install it using the following command.

`apt install python3.8-venv`{{exec}}


We would need to generate a new Pulumi project using the following command.

`pulumi new python`{{exec}}

Pulumi have API keys that are used to authenticate with the Pulumi service. You can create a new API key by visiting the Pulumi console and clicking on the `New Access Token` button. You can then enter a name for the token and click on the `Create` button. This will generate a new API key that you can use to authenticate with the Pulumi service.

I have set up a token for you to use in this tutorial.
`pul-a58665e22fec1b6808b11da5ae13e4e000957867`{{copy}} 
(This token is valid for only a week for assign tasks, you should create your own token for your projects)

This would prompt you to enter a project name. You can enter any name you like. For this example, we will use `docker-container`.

Now we will be asked to enter the stack name. A stack is a deployment environment. For this example, we will use `dev`.

This will create a new Pulumi project with the following files:

- `Pulumi.yaml`: This file contains the project configuration.

- `main.py`: This file contains the Pulumi program.

- `requirements.txt`: This file contains the Python dependencies.

As we using a virtual environment (which is recommended for Python projects), ensure it is activated. You can activate it with

`source venv/bin/activate`{{exec}}

We will install the pulumi_docker package using the following command.

`pip install pulumi_docker`{{exec}}

Next, we will write the Pulumi program in the `Pulumi.py` file. The program will create a Docker image and container running an nginx server. The nginx server will be accessible on port 8000.

```
import pulumi
import pulumi_docker as docker

# Use the official Nginx Docker image from Docker Hub
nginx_image = docker.RemoteImage("nginx_image",
    name="nginx:latest"
)

# Create a Docker container running Nginx
nginx_container = docker.Container("nginx_container",
    image=nginx_image.name,
    ports=[
        docker.ContainerPortArgs(
            internal=80,  # Internal container port
            external=80,  # External host port
        )
    ],
)

# Export the container ID as an output
pulumi.export("container_id", nginx_container.id)
```

`pulumi up`{{exec}}

Prompt to ask for confirmation to deploy the stack. Accept yes to update and deploy the stack.

The program will create a Docker image and container. It will also output the container name and port. You can access the nginx server by visiting 

```
docker images
docker ps
curl 127.0.0.1:80
```


