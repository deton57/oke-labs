## Welcome to part 4 - Monitoring using Rancher ## 

In this part, we are going to activate and monitor our cluster and services,
using Rancher, we are going to monitor the:

* The Cluster
* The Deployment
* The Nodes
* The Pods

We are going to load the Wordpress service, and scale out some pods from Rancher.
And we are goint to look into the built-in Grafana, that Rancher will deploy, in order
to get clear picture of what exactly is happening, based on the: Network, CPU and Storage workloads. 


Before we can view anything in the monitoring screen, 
we need to enable the monitoring feature.

## Enabling the monitoring ## 

1. Go to the global menu:

![image]()

2. Now click on your cluster name: 

![image]()

3. Go to Tools > Monitoring:

![image]()

4. Here you will have a menu, with some Prometheus and Grafana settings,
let's scroll to the bottom of the page and click on "Enable":

![image]()

It will take some time, while the Grafana and Prometheus are being deployed.

Go to your project by clicking on the top left menu - 
cluster name, and in the dropdown menu click on the project name:

![image]()

Now go to Resources > Workloads:

![image]() 

You will know that the monitoring is not up yet, because we don't see a Grafana icon, and 
we don't see the green bars: 

![image]()

If you wait a while, usually 2-5 minutes, 
you will see the bars and the Grafana icon: 

![image]()

Now monitoring is up! 

## Running load test ##

Next we are going to run a load test. 

1. Choose the Wordpress workload: 

![image]()

2. Leave 2 tabs open:
1. Pods
2. WorkLoads Metrics

![image]()

2. You can scale out easily, some pods, by click on the + button above: 

![image]()

This will create additional pods, in order to split the load between them. 

3. Under the Workloads Metrics, you can change the display time to 5 minutes. 

![image]() 

4. It's time to start the test. 
For this you will need your Wordpress endpoint IP Address.
** In case you forgot it, from the Rancher menu, go to Apps > click on wordpress and copy one of the endpoints URL ** 
Open Mobaxterm and SSH to your machine.

from the terminal, run the following command: 

```ab -c 100 -n 10000 https://<your-wordpress-endpoint-ip-address>/```

-c = Number of multiple requests to make at a time
-n = Total number of requests. 

if you run the command successfully, you should see the following output: 

```
This is ApacheBench, Version 2.3 <$Revision: 1430300 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 158.101.180.218 (be patient)
Completed 1000 requests
```

5. Go back to Rancher and click on the refresh button, under workloads.

![image]()

You should see now the load being generated: 

![image]()

6. It's time to scale some pods out, let's add another 3 pods, so we will have a total of 6: 

![image]() 

7. Wait until all the poads, will finish initializing and refresh the workload again.

![image]()

Now you will see that the load does not grow the in the same pace as before. 

![image]() 

8. Click on the Grafana icon: 

![image]()

It will open a new tab of Grafana screen, click on the Home (Top left corner): 

![image]() 


