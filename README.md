# Welcome to Machine Learning Day 2019!

The aim of this all-day workshop is to familiarize you with the Microsoft Azure public cloud and some of its Big Data and Machine Learning technologies. 

By the time you leave the workshop, you should know the following:
- How to navigate Azure and how to spin up new resources to do your work
- Know different data collection & sanitation techniques and technologies
- Have a feel for implementation of machine learning platforms that will facilitate your research aspirations
- How to have fun working with scaled, (almost) unlimited cloud resources

## Getting Started 

These steps will get your started with a fresh start. If at all possible, please try to have these pre-requisites complete before the lab.

### Install Command-Line Tools and Integrated Development Environment (IDE)

1. Install the cross-platform [Azure Command-Line Interface (CLI)](http://aka.ms/installCLI)  

	*Optional: IF you don't want to use the native web-based Azure Cloud Shell and want to use your own computer instead*
2. Install the cross-platform [Visual Studio Code](https://code.visualstudio.com/Download) 

	*Optional: It makes it easier if you have this installed as your .JSON file editor as it marks all sorts of files cleanly and has great GitHub integration*

<br>
<i/> Optional: Install GitHub to Download ML Day Materials </i>
<br><br>
https://desktop.github.com/

## Please install these pre-requisites when you login


### Please execute the following scripts inside your Azure portal using the BASH [Azure Cloud Shell](https://docs.microsoft.com/en-us/azure/cloud-shell/overview)


***Tip: Copy and paste these blocks of code together
```azurecli
read -p "Enter Your Student Number: " stunum # This is your Resource Group Number listed at portal.azure.com --> Resource Groups link
```
```
echo "Your Student Number is" $stunum
stoacct=ml2019stu$stunum
stocont=hadooplabs
sturg="Student$stunum"
curl -o weblogs.csv https://raw.githubusercontent.com/Microsoft/code-challenges/master/Labs/Azure%20HDInsight/HiveLab/Data/hadooplabs/Lab1/weblogs.csv
````
```
az storage account create --resource-group $sturg --location eastus --name $stoacct --sku Standard_LRS 
```
```
az storage container create  --name hadooplabs --account-name $stoacct
az storage container create  --name $stoacct --account-name $stoacct

```
```
stokey=$(az storage account keys list --account-name $stoacct --query [0].value | tr -d '"')
```
```
azcopy --source weblogs.csv --destination https://$stoacct.blob.core.windows.net/$stoacct/hadooplabs/Lab1/weblogs.csv --dest-key $stokey
```
```
az group deployment create --name HDIdeploy --resource-group $sturg --template-uri "https://raw.githubusercontent.com/kfprugger/MLDay/master/HDInsightProvision/template.json" --parameters "clusterName=ml2019stu$stunum" 'clusterType=hadoop' 'clusterLoginUserName=azure' 'sshUserName=azure' "storageAccount=$stoacct" 
```
# Now let's take a look at the agenda for the day

### Session 1: Introduction to Azure and Azure Fundamentals 

- **0830-0930:** This session gives a quick overview of Azure, how we will interacting with the different technologies of the day, and which Big Data and Machine Learning technologies we will be using.

### Session 2: IoT Ingestion and Data Collection
- **0930-1030:** We will start our first lab with looking at methods on how to collect large data sets for analysis. We'll start with an IoT simulator to simulate large data sets coming into your Azure subscription. In the following sessions, we'll learn how to sanitize and then analyze these large amounts of data

- [IoT Hand-On Lab](https://docs.microsoft.com/en-us/learn/modules/manage-iot-devices/)

### Session 3: Azure Machine Learning Studio Lab and Data Sanitation
- **1045-1145:** Our second lab will analyze and sanitize a large amount of data similar to what we generated in Lab 1. Our objective is to visualize this large dataset, sanitize it and then infer predictions based on the previously collected data using a ML algorithm.

- [Azure ML Studio Hands-On Lab](https://github.com/kfprugger/MLDay/blob/master/MLStudio/create-experiment.md#open-machine-learning-studio)

### Session 4: HDInsight (Hadoop Made Easy)
- **1230-1330:** Our third lab creates a HIVE table in Hadoop, one of the most prominent open-source big data & analytics engine, and demonstrates how to manipulate large amounts of data -- in this case weblogs -- and make sense of it with minimal effort

- [HDInsight Hands-On Lab](https://github.com/kfprugger/MLDay/blob/master/Azure%20HDInsight/HiveLab/hands-on-lab.md)

### Session 5: Databricks (Apache Spark ML Made Easier)
- **1330-1430:** This lab will setup a Databricks workspace. Databricks a hosted Apache Spark environment that is simplified so that minimal infrastructure knowledge is needed to leverage the platform in order to employ Spark Machine Learning or Big Data notebooks.

- [Databricks Setup and Lab 1 Hands-On Lab](https://github.com/kfprugger/MLDay/blob/master/DatabricksML/HOL%20step-by%20step%20-%20Cognitive%20services%20and%20deep%20learning.md#exercise-1-setup-azure-databricks-workspace)
  - Exercise 1 and Exercise 2

### Session 6: Cognitive Services (pre-trained ML), Data Lakes and Deep Neural Networks
- **1445-1600:** In Exercise 3, we'll use the opensource TensorFlow ML library to analyze the data even further by using deploying a simple Deep Neural Network which will classify claims data.
  
  If we have time, Exercise 4 leverages pre-built, compiled and inexpensive public Azure services to analyze the text with Microsoft's Text Analytics API which is part of the Cognitive Services toolkit. These services can be leverage in ANY code, anywhere securely so long as the code has access to the internet.

- [Azure Databricks + TensorFlow Hands-On Lab](https://github.com/kfprugger/MLDay/blob/master/DatabricksML/HOL%20step-by%20step%20-%20Cognitive%20services%20and%20deep%20learning.md#exercise-3-create-and-deploy-a-tensorflow-model)
  - Exercise 3 & 4 (if you have time)
