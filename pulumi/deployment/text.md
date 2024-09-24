We will used Python to write the Pulumi program. Also we will use the pulumi_docker package to create the Docker image and container.

`pip install pulumi_docker`{{exec}}

It said that there are some conflict with the package. We will install the package using the following command.

`pip install semver~=2.13`{{exec}}

Let's create a simple Pulumi progam that running ngix on port 8000 on the system. So just make a new python file and write the following code.

```
import pulumi
from pulumi_docker import Image, Container, DockerBuild

nginx_image = Image("nginxImage",
    image_name="nginx:latest",
    build=DockerBuild(context=".")
)

# Create the Docker container
nginx_container = Container("nginxContainer",
    image=nginx_image.image_name,
    name="tutorial",
    ports=[{
        "internal": 80,
        "external": 8000,
    }]
)

# Export the container name and port as outputs
pulumi.export("container_name", nginx_container.name)
pulumi.export("container_port", nginx_container.ports) 
```{{copy}}

We should validate the program before running it. Run the following command to validate the program. This automatically download and configure the necessary providers

`pulumi preview`{{exec}}

If the validation is successful, we can run the program using the following command.

`pulumi up`{{exec}}

The program will create a Docker image and container. It will also output the container name and port. You can access the nginx server by visiting 

```
docker images
docker ps
curl 127.0.0.1:8000
```

You can view the file to see the objects that Pulumi created.

`cat Pulumi.dev.yaml`{{exec}}

Now let us clean up the resources by running the following command.

`pulumi destroy`{{exec}}