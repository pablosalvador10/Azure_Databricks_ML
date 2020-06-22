# Azure_databricks_ML


Here is how you can use the Databricks dbutils commands. Databricks has a secret management utility built inside, so we need to use that to make the secrets work in Databricks.


Step 1 –
Use the Azure CLI from the azure portal. It will be here as shown in the screenshot:
 

Follow these commands in the CLI:

Create a virtual python env - 
               
virtualenv -p /usr/bin/python2.7 databrickscli
               
activate the created virtual python env and install databricks cli-
               
source databrickscli/bin/activate
               
pip install databricks-cli

Now open Databricks and grab the token, like this:

 

 
 

Replace the lifetime to nothing to make the token work infinitely. After generating, copy the token and save it at a safe place for future use.
Now using the CLI again, type in these commands and follow the instructions for the token configuration:

databricks configure –token
(here the host will be the databricks website link)

Create any scope, similar to this which we used for prod databricks environment:
databricks secrets create-scope --scope dlsanalyticsprodsecretscope

databricks secrets put --scope dlsanalyticsprodsecretscope --key dlsanalyticsprodkey

Check you created secrets with this command:
databricks secrets list --scope dlsanalyticsprodsecretscope

Now use this scope name and secret name inside Databricks to make the command work. We use something like this in our notebooks:
 
