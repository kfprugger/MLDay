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


***Tip: Copy and paste these line-by-line
```azurecli

read -p "Enter Your Student Number: " stunum
stoacct=ml2019stu$stunum
stocont=hadooplabs
sturg="Student$stunum"

curl -o weblogs.csv https://raw.githubusercontent.com/Microsoft/code-challenges/master/Labs/Azure%20HDInsight/HiveLab/Data/hadooplabs/Lab1/weblogs.csv


echo "Your Student Number is" $stunum




az storage account create --resource-group student$stunum --location eastus --name ml2019stu$stunum --sku Standard_LRS 

az storage container create  --name hadooplabs --account-name $stoacct


stokey=$(az storage account keys list --account-name $stoacct --query [0].value | tr -d '"')




curl -o parameters.json 'https://raw.githubusercontent.com/kfprugger/MLDay/master/HDInsightProvision/parameters.json'


az group deployment create --name HDIdeploy --resource-group $sturg --template-uri "https://raw.githubusercontent.com/kfprugger/MLDay/master/HDInsightProvision/template.json" --parameters 'clusterName=rojo1111' 'clusterType=hadoop' 'clusterLoginUserName=azure' 'sshUserName=azure'

```
<br>
<b/> Session 2: </b>
