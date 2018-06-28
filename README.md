# Weekly challenge

## Challenge
> have you heard about AWS Cloudformation? Well if you haven’ t it’s okay. I propose to write a GCP’s Cloud Deployment Manager template. This template would have to spin up an instance that could only be accessible from OCTO’s IP.

## Solution
GCP multifile deployment template is created. Following files are created:
- template.yaml - deployment configuration itself
- compute.jinja - aggregating template for all resources in deployment
- instance.jinja - VM instance template. Creates VM and attaches it to default network. Sticks 'weekly-challenge' tag on it 
- firewall.jinja - firewall rules template. Creates 1 allow rule for OCTO IP address and 1 deny rule for all other addresses. Applies only to resources (VMs) with 'weekly-challenge' tag

## Deployment
To create a deployment, just run following command from the project's root folder

```gcloud deployment-manager deployments create weekly-challenge-deployment --config template.yaml```