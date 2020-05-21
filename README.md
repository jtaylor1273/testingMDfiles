# Azure Kubernetes Service 
The Azure Kubernetes Service solution is used to provision AKS in a customer environment for the first time. There are a number of default selections that the Engineer should adjust to fit the customer request specifically.


# Required Services
AKS has a number of dependant services that should be created prior to starting the template below
- Container Image - this image will be created using a [Docker File](https://docs.docker.com/engine/reference/builder/) and submitted to the ACR.
- [Azure Container Registry](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-get-started-docker-cli) - this is where images are stored for use by AKS
- [Azure Log Analytics Workspace](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/container-insights-overview?toc=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Faks%2Ftoc.json&bc=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fbread%2Ftoc.json) - this is where metric and logging information will be stored for AKS
     

# How to run this solution
1. Collect Information needed about container registry 
2. Modify the azuredeploy.parameters.json file (Information on these resource parameters are [here!](https://docs.microsoft.com/en-us/azure/templates/microsoft.containerservice/2020-03-01/managedclusters)
   * resourceName
   - location
   - dnsPrefix
   - kubernetesVersion
   - networkPlugin
   - enableRBAC
   - enablePrivateCluster
   - enableHttpApplicationRouting
   - vmssNodePool
   - workspaceName
   - omsWorkspaceID
   - workspaceRegion
   - acrName
   - acrResourceGroup
3. Review the default values in the azuredeploy.json file to ensure your deployment will be correct
4. Execute the following PowerShell command to deploy

```
New-AzResourceGroupDeployment -ResourceGroupName "RGName" `
  -TemplateFile "<filelocation>\azuredeploy.json"  `
  -TemplateParameterFile "<filelocation>\azuredeploy.parameters.json"
```
