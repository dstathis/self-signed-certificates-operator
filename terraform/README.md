# Self-Signed-Certificates Terraform Module 

This Self-Signed-Certificates Terraform module aims to deploy the [self-signed-certificates charm](https://charmhub.io/self-signed-certificates?channel=latest/beta) via Terraform.

## Getting Started

### Prerequisites

The following software and tools needs to be installed and should be running in the local environment.

- `microk8s`
- `juju 3.x`
- `terrafom`

### Deploy the self-signed-certificates charm using Terraform

Make sure that `storage` plugin is enabled for Microk8s:

```console
sudo microk8s enable hostpath-storage
```

Add a Juju model:

```console
juju add model <model-name>
```

Initialise the provider:

```console
terraform init
```

Customize the configuration inputs under `terraform.tfvars` file according to requirement.

Replace the variable in the `terraform.tfvars` file:

```yaml
model_name =<your model-name>
```

Run Terraform Plan by providing var-file:

```console
terraform plan -var-file="terraform.tfvars" 
```

Deploy the resources, skip the approval:

```console
terraform apply -auto-approve 
```

### Check the Output

Run `juju switch <juju model>` to switch to the target Juju model and observe the status of the application.

```console
juju status
```

### Clean up 

Remove the application:

```console
terraform destroy -auto-approve
```
