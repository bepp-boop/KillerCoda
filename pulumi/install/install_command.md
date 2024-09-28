### Install Pulumi
To install Pulumi using a script, you can use the following command:


`curl -fsSL https://get.pulumi.com | sh`{{exec}}

Restart your terminal to ensure the pulumi command is available.

### Activate Pulumi in Your Current Session

To make the `pulumi` command immediately available in your current terminal session, run:

`exec $SHELL`{{exec}}

This command reloads your shell, ensuring that the newly installed Pulumi is accessible without needing to open a new terminal window.

We can confirm installation by running on new tab:

`pulumi version`{{exec}}

