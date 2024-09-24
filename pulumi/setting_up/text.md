Check that containerd is running and exposed on your syst
`systemctl status containerd --no-pager`{{exec}}

Check that containerd is listening on the default port:
`ss -tulnp | grep containerd`{{exec}}

Made directory for the containerd configuration:
`sudo mkdir -p /root/learn-pulumi-docker-container`{{exec}}
`cd /root/learn-pulumi-docker-container`{{exec}}

Check if other container is running.
`docker ps`{{exec}}


