# Cloudy With A Chance Of Integration

These CloudFormation scripts are used to spin up test infrastructure.

# KOPS Cluster

This script can be saved to display a summary after the KOPS cluster has been provisioned:

```
Write-Host "Worker IP address: $($OctopusParameters["Octopus.Action[Kubernetes Infrastructure].Output.AwsOutputs[PublicIp]"])"
Write-Host "Useful commands"
Write-Host "kops create cluster --dns private --zones=us-east-1c $($OctopusParameters["Octopus.Action[Kubernetes Infrastructure].Output.AwsOutputs[DomainName]"])"
Write-Host "kops update cluster $($OctopusParameters["Octopus.Action[Kubernetes Infrastructure].Output.AwsOutputs[DomainName]"]) --yes"
Write-Host "kops delete cluster $($OctopusParameters["Octopus.Action[Kubernetes Infrastructure].Output.AwsOutputs[DomainName]"]) --yes"
Write-Host "kubectl run echo-node --image=tutum/hello-world --port=80"
Write-Host "kubectl expose deployment echo-node --type=NodePort"
Write-Host "kubectl describe service echo-node"
Write-Host "kubectl expose deployment echo-node --target-port=80 --name=echo-node --type=LoadBalancer"
Write-Host "You will also want to open ports 30000-32767 in the security group"
```