Verify containerd service status and accessibility:
`systemctl status containerd --no-pager`{{exec}}

Confirm containerd is listening on its default port:
`ss -tulnp | grep containerd`{{exec}}

Create and navigate to the directory for containerd configuration:
`sudo mkdir -p /root/learn-pulumi-docker-container`{{exec}}
`cd /root/learn-pulumi-docker-container`{{exec}}

Check for any running Docker containers:
`docker ps`{{exec}}


