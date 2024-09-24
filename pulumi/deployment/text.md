We will used Python to write the Pulumi program. Also we will use the pulumi_docker package to create the Docker image and container.

We also need this package to be installed on our system. We can install it using the following command.

`apt install python3.8-venv`{{exec}}



We would need to generate a new Pulumi project using the following command.

`pulumi new python`{{exec}}

This will create a new Pulumi project with the following files:

- `Pulumi.yaml`: This file contains the project configuration.

- `Pulumi.py`: This file contains the Pulumi program.

- `requirements.txt`: This file contains the Python dependencies.

We will install the pulumi_docker package using the following command.

`pip install pulumi_docker`{{exec}}

Next, we will write the Pulumi program in the `Pulumi.py` file. The program will create a Docker image and container running an nginx server. The nginx server will be accessible on port 8000.

```python
import pulumi
import pulumi_docker as docker

# Define the nginx container
nginx_container = docker.Container(
    'nginx-container',
    image='nginx:latest',
    ports=[{
        'internal': 80,
        'external': 8000
    }]
)

pulumi.export('nginx_ip', nginx_container.ports[0].apply(lambda p: p['host']))
```

`pulumi up`{{exec}}

The program will create a Docker image and container. It will also output the container name and port. You can access the nginx server by visiting 

```
docker images
docker ps
curl 127.0.0.1:8000
```


