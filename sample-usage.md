## Using the Azure CLI 2.0 to create an ACS cluster

You can install the Azure CLI 2.0 using the instructions provided [here](https://github.com/Azure/azure-cli).

### Login to your account
```
az login 
```
You will need to go this [link](https://login.microsoftonline.com/common/oauth2/deviceauth) to authenticate with the code provided in the CLI.
![type command](https://github.com/sauryadas/Az-py-cli-acs/blob/master/media/login.png)
![browser](https://github.com/sauryadas/Az-py-cli-acs/blob/master/media/login-browser.png)

### Create a resource group
```
az resource group create -n acsrg1 -l "westus"
```
![Image resource group create](https://github.com/sauryadas/Az-py-cli-acs/blob/master/media/rg-create.png)


### List of available ACS commands
```
az acs -h
```
![ACS command usage](https://github.com/sauryadas/Az-py-cli-acs/blob/master/media/acs-command-usage-help.png)


### Create an Azure Container Service Cluster

*ACS usage in the CLI
```
az acs -h
```
The name of the container service, the resource group created in the previous step and a unique DNS name are mandatory. 
Other inputs are set to default values(please see help below)unless overwritten using their respective switches.
![Image ACS create help](https://github.com/sauryadas/Az-py-cli-acs/blob/master/media/create-help.png)

```
az acs create -n acs-cluster -g acsrg1 -d applink789
```
After you type the above command, wait for about 10 minutes for the cluster to be created.
![Image ACS create](https://github.com/sauryadas/Az-py-cli-acs/blob/master/media/cluster-create.png)


### List ACS clusters in a resource group
```
az acs list -g acsrg1 --output table
```
![Image ACS list](https://github.com/sauryadas/Az-py-cli-acs/blob/master/media/acs-list.png)


### Display details of a container service cluster
```
az acs show -g acsrg1 -n acs-cluster --output list
```
![Image ACS list](https://github.com/sauryadas/Az-py-cli-acs/blob/master/media/acs-show.png)


### Scale the ACS cluster
*Both scaling in and scaling out are allowed. The paramater new-agent-count is the new number of agents in the ACS cluster
```
az acs scale -g acsrg1 -n acs-cluster --new-agent-count 4
```
![Image ACS scale](https://github.com/sauryadas/Az-py-cli-acs/blob/master/media/acs-scale.png)

### Delete a container service cluster
```
az acs delete -g acsrg1 -n acs-cluster 
```
