﻿---
title:  "Retrying a processflow"
toc: true
tag: developers
category: "Processflow"
menus: 
   quickstartprocessflow:
        title: "Retrying a processflow"
        weight: 7
        icon: fa fa-file-word-o
        identifier: retryprocessflow
---

Execution of a processflow is vital process for transforming data from source to 
destination application. In real-time, execution of processflow may fetch errors 
with respect to data configurations. 
processflow Retry is a feature that can Resync the data after rectifying the error 
such that no data loss occurs with respect to the sync process. processflow Retry 
can be configured both Manually and in Auto-Mode.

## Prerequisites for processflow Retry (in Auto-Mode)
* You need to [create a processflow](/processflow/creating-processflow/).   
* You need to [deploy](/processflow/deploying-and-executing-processfloww/) the created processflow or an existing process that needs to be executed. 
* [Environment](/deployment/Environment-Management/) should be active for the processflow to execute successfully.
* You need to execute a processflow for implementing Retry. 

## Steps to configure Auto-Retry:
1.	Navigate to the processflow designer page and Deploy/Redeploy a processflow.    
2.	Click on the `Deploy button` in the designer page. The [deploy](/processflow/deploying-and-executing-processfloww/) wizard opens.    
3.	Configure the settings for deploying the processflow and navigate to the `Sync & Retry` section of deploy wizard.     
![Processflow Retry1](../../../staticfiles/processflow/media/processflow-retry1.png)      
4.	By default, the `Retry toggle button` will be in` manual mode` when deploying for the first time. Switch the `toggle button` to the `auto mode` to view the configurational panel of Auto Retry.  
![Processflow Retry2](../../../staticfiles/processflow/media/processflow-retry2.png)      
5.	You need to select the frequency of the autosync from the drop-down. You can setup the configuration as per the following options.  
* Every Day  
* Hour     
![Processflow Retry3](../../../staticfiles/processflow/media/processflow-retry3.png)      
6.	On keeping the frequency in `Every Day`, you get the option for providing Retry Daily At. You can configure the resync schedule timing by clicking on the Clock Icon beside the Retry Daily at Field. 
![Processflow Retry4](../../../staticfiles/processflow/media/processflow-retry4.png)      
7.	On selecting the Frequency either as `Everyday or Hourly`, you get these Following common fields.      
(a) Interval: This determines the pause time or break time of the Retry Activity. The interval is hourly basis, if selected 2 , the Interval time of fetching retry data will be of 2hrs.     
    Interval time can be selected from 1-23 only.    
(b) Time Lapse: This determines the execution time of the set of errored data and will execute the Retry based on its previous attempts. The time lapse is based on Minutes.      
(c) Batch Size: This defines the number of data  that will be Resynced in one batch.    
For an Instance: If a set of data is failed at 14:00 hrs, and the Time lapse selected as 20mins. The failed data will be activated for retry after 14:20 hrs. And if the Interval is set at 1hr, the execution of the Retry sync of those failed data happen at 15:00 hrs, if the Deployment Time and the first execution was made at 14:00 hrs.      
8.	After configuring the Auto-Retry, click on the Deploy button. Execute the designed processflow.
 **You can execute the processflow both in Manual or in Auto-Mode even if processflow Retry is configured as Auto.**
9.	Navigate to the Manage > Environment for viewing the Resync Bucket of Retry, for the executed processflow.
**You need have the environment active for viewing the details page, You can troubleshoot a [detached or a disconnected agent](/deployment/Environment-Management/#detaching-and-attaching-environment).** 
10.	Click processflows Tab. You can view the list of all the deployed processflows. Following are the details that will display for each deployed processflows.
* Name of the processflow  
* The time of Deployment   
* Actions    
![Processflow Retry5](../../../staticfiles/processflow/media/processflow-retry5.png)    
11.	Click Ellipses button (...) available beside the processflow that you have executed. You can view the Retry button available in the context menu.  
![Processflow Retry6](../../../staticfiles/processflow/media/processflow-retry6.png)    
12.	The Resync Bucket of the Retry Window opens. You can view the following details in the Rety Window:
- Name: You will be able to view the name of the processflow in the Header Panel.
- Environment Name: You will be able to view the Environment Name, on which the PF is deployed.
- Description: You can also view the description of the processflow.
- Resync Button: You can manually Resync the failed data by selecting the record and clickin on the Resync Button.
- Filter Button: You can also filter the failed records by click on the Filter icon.
![Processflow Retry7](../../../staticfiles/processflow/media/processflow-retry7.png)    
13.	You can filter the data in the list using the contents of the Source ID by click on the filter icon.
![Processflow Retry8](../../../staticfiles/processflow/media/processflow-retry8.png)    
14.	You can view the list of the Failed items along with the following set of informations.
* Node Name: You will be viewing the app name used in the GET node.
* Source Id : The Ids of the failed item fetched from the Source App will be displayed in this Column.
* Status: The status of the all the data failure/Success will be displayed in the bucket.
* Time Stamp: You will be viewing the time stamp of the last execution.
* Tries: You would be viewing number of tries that has been attempted to resync a failed data. 
 ![Processflow Retry9](../../../staticfiles/processflow/media/processflow-retry9.png)    
**Note: For Auto-Retry, each data will be Retried 4 times excluding the main execution.**
15.	You can also Resync the failed data manually, after auto-retry has made its attempts, by selecting the check boxes and clicking on the **RESYNC** button. 

**Note:** You can either select all the data by enabling the checkbox beside `Node Name` or you can individually select checkbox, for executing the Resync Process for selective data. 

![Processflow Retry10](../../../staticfiles/processflow/media/processflow-retry10.png)    

Following the above process, you can successfully implement Auto-Retry and view the data in the Resync Bucket of the Auto-Retry window.

**Protip**  For every Retry process (Both Auto/Manual), you will be generated with a [Snapshot](/processflow/snapshot-processflow/). 
{: .notice--info}

