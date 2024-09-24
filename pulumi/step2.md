### Pulumi & Google Cloud: Before you begin

setup your environment correctly

> curl -fsSL https://get.pulumi.com | sh

test to see if it is installed correctly and check the version

> pulumi version
you will get 
> v3.134.0
if this doesnt work, you will need to restart your terminal.

Configure Pulumi to acces your Google Cloudaccount using IAM account or a service account that has a PRogrammatic acces.

If google cloud is not configured to interact with your Google Cloud project, set it with the config command using the project’s ID:

>gcloud config set project <YOUR_GCP_PROJECT_ID>


Next, Pulumi requires default application credentials to interact with your Google Cloud resources, so run auth application-default login command to obtain those credentials.

> gcloud auth application-default login