# Azure Kubernetes Service 
The Azure Kubernetes Service solution is used to provision AKS in a customer environment for the first time. There are a number of default selections that the Engineer should adjust to fit the customer request specifically.


# Required Services
AKS has a number of dependant services that should be created prior to starting the template below
- Azure Container Registry - this is where images are stored for use by AKS
- Azure Log Analytics Workspace - this is where monitoring information will be stored for AKS
     
     
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
