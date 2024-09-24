Let's create a simple Pulumi progam that running ngix on port 8000 on the system.


`vi main.py`{{copy}}

We will used Python to write the Pulumi program. Also we will use the pulumi_docker package to create the Docker image and container.

`pip install pulumi_docker`{{exec}}

It said that there are some conflict with the package. We will install the package using the following command.

`pip install semver~=2.13`{{exec}}

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

