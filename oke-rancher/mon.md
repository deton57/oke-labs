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

8. Let's wait till the load test will finish running, 
we should get the following output: 

```
This is ApacheBench, Version 2.3 <$Revision: 1430300 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 158.101.180.218 (be patient)
Completed 1000 requests
Completed 2000 requests
Completed 3000 requests
Completed 4000 requests
Completed 5000 requests
Completed 6000 requests
Completed 7000 requests
Completed 8000 requests
Completed 9000 requests
Completed 10000 requests
Finished 10000 requests


Server Software:        Apache/2.4.41
Server Hostname:        158.101.180.218
Server Port:            443
SSL/TLS Protocol:       TLSv1.2,ECDHE-RSA-AES256-GCM-SHA384,2048,256

Document Path:          /
Document Length:        38007 bytes

Concurrency Level:      100
Time taken for tests:   244.423 seconds
Complete requests:      10000
Failed requests:        4801
   (Connect: 0, Receive: 0, Length: 4801, Exceptions: 0)
Write errors:           0
Total transferred:      464375589 bytes
HTML transferred:       461515589 bytes
Requests per second:    40.91 [#/sec] (mean)
Time per request:       2444.229 [ms] (mean)
Time per request:       24.442 [ms] (mean, across all concurrent requests)
Transfer rate:          1855.36 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        3   71 267.2      8    2844
Processing:    51 2363 2991.6   1502   18941
Waiting:       28 1275 1381.2    973    9070
Total:         56 2435 3051.7   1566   18961

Percentage of the requests served within a certain time (ms)
  50%   1566
  66%   2086
  75%   2559
  80%   3083
  90%   6483
  95%   9857
  98%  13031
  99%  14759
 100%  18961 (longest request)
```

9. Go to Rancher and click on the Grafana icon: 

![image]()

It will open a new tab of Grafana screen, click on the Home (Top left corner): 

![image]() 

Change it to Deployment.

![image]() 

Change the time on the top right corner to 30 minutes: 

![image]() 

Now you will see some metrics regarding the deployment, 
hover over the metrics, to see what happened during the load test.

10. Change the the dashboard to Nodes on the top left corner and the time to 30 minutes:

![image]() 

Now you will see some metrics regarding nodes, 
hover over the metrics, to see what happened during the load test.

10. Change the the dashboard to Pods on the top left corner and the time to 30 minutes:

![image]() 

Now you will see some metrics regarding pods, 
hover over the metrics, to see what happened during the load test.


Congratulations, you finished the lab. 
Now you know how to deploy and operate a cluster from Rancher.
You know how to monitor and scale the deployment. 

Wait for some more advanced labs in the future.

