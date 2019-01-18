# Let's Start With Some Pre-Reqs

These steps will get your started with a fresh start. If at all possible, please try to have these pre-requisites complete before the lab.

## Install Command-Line Tools and Integrated Development Environment (IDE)

1. Install the cross-platform [Azure Command-Line Interface (CLI)](http://aka.ms/installCLI) 



2. Install the cross-platform [Visual Studio Code](https://code.visualstudio.com/Download) 

<br>
<i/> Optional: Install GitHub to Download ML Day Materials </i>
<br><br>
https://desktop.github.com/

## Now let's take a look at the agenda for the day

<b/> Session 1: </b>Introduction to Azure and Azure Fundamentals (install the pre-reqs and install the foundational compute resources)
### Please execute the following scripts inside your Azure portal using the BASH [Azure Cloud Shell](https://docs.microsoft.com/en-us/azure/cloud-shell/overview)
```azurecli

Read prompt "What's your student number"

az storage create $prompt....

curl -o parameters.json 'https://raw.githubusercontent.com/kfprugger/MLDay/master/HDInsightProvision/parameters.json'

az group deployment create --name HDIdeploy --resource-group LabPrototyping --template-uri "https://raw.githubusercontent.com/kfprugger/MLDay/master/HDInsightProvision/template.json" --parameters @parameters.json
```
<br>
<b/> Session 2: </b>
