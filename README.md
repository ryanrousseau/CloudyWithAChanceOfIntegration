# Cloudy With A Chance Of Integration

These CloudFormation scripts are used to spin up test infrastructure.

# KOPS Cluster

This script can be saved to display a summary after the KOPS cluster has been provisioned:

```
Write-Host "Useful commands"
Write-Host "/opt/kops kops create cluster --zones=us-east-1c  $($OctopusParameters["Octopus.Action[Kubernetes Infrastructure].Output.AwsOutputs[DomainName]"])"
Write-Host "/opt/kops create secret --name $($OctopusParameters["Octopus.Action[Kubernetes Infrastructure].Output.AwsOutputs[DomainName]"]) sshpublickey admin -i ~/.ssh/id_rsa.pub"
Write-Host "/opt/kops update cluster $($OctopusParameters["Octopus.Action[Kubernetes Infrastructure].Output.AwsOutputs[DomainName]"]) --yes"
Write-Host "/opt/kops delete cluster $($OctopusParameters["Octopus.Action[Kubernetes Infrastructure].Output.AwsOutputs[DomainName]"]) --yes"
```