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

**Enabling the monitoring** 

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




