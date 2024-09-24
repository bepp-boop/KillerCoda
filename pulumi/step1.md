### Install Pulumi on Linux
To install Pulumi using a script, you can use the following command:

`curl -fsSL https://get.pulumi.com | sh`{{exec}}

We can confirm installation by running on new tab:

`pulumi version`{{exec}}



### Install Pulumi on Windows
You can install Pulumi using elevated permissions through the Chocolatey package manager

> choco install pulumi

this wil install pulumi CLI to the usual place (often $($env:ChocolateyInstall)\lib\pulumi)

to update Pulumi 

> choco upgrade pulumi


you can specify which version of pulumi you want to install by

> choco install pulumi --version <version>


### Install Pulumi on Mac

To install pulumi on macOS 

 > curl -fsSL https://get.pulumi.com | sh -s -- --version <version>