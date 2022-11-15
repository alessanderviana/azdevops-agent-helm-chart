# Disclaimer
Run this at your own risk.

Create a Helm Chart with a Azure pipeline agent to run Azure DevOps CI/CD automations in your own kubernetes cluster.

## Prerequisites
- Have a kubernetes cluster or similar running
- Knowledge how to install applications on kubernetes through Helm utility
- Knowledge how to build a Docker image from a Dockerfile (optional)
- Knowledge how to send a Docker image to a container registry (optional)

# How to run
You can build your own Docker image and push it to your image repo or you can use mine **ale55ander/arm64-azure-pipeline-agent:latest**.

> To change the O. S. Arch, change the parameter TARGETARCH at the Dockerfile

The command below runs the test.
```sh
helm upgrade -i azdevops-agent ./ \
  -f values-azagent.yaml \
  --set configEnv.AZP_POOL=YOUR_AZ_DEVOPS_POOL \
  --set secretEnv.AZP_URL=https://THE_ADDRESS_OF_YOUR_AZURE_DEVOPS_SUBSCRIPTION \
  --set secretEnv.AZP_TOKEN=YOUR_AZURE_DEVOPS_TOKEN \
  --namespace azdevops \
  --create-namespace \
  --dry-run
```

To really apply the changes, remove the --dry-run parameter.