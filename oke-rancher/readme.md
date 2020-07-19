Welcome to OKE - Rancher lab.

Our goal will be to get familiar with Kubernetes solution on Oracle cloud,
and Rancher, as an open source tool that can manage the Kubernetes. 


prerequisite - before you being make sure you have Oracle OCI account.
Sign in page: https://www.oracle.com/cloud/sign-in.html
If you don't have a cloud account, you can create a free trial here: 
<URL>


Lab steps: 

First thing we will do is prepare a virtual machine with Oracle Developer image,
and prepare our cloud, so we can connect to the machine and launch a Rancher Docker.

1. [Create a virtual machine with Rancher installed on Docker](vm.md) 

After we have a Rancher installed, 
we will create an OKE cluster on cloud. 

2. [Create an OKE cluster using Rancher](cluster.md)

We have a cluster up and running with nodes, 
now it's time to install apps on the cluster. 

3. [Install Wordpress app from Rancher catalog and manage it](wp.md)

Our apps are up and running, let's monitor them. 

4. [Monitoring the cluster and the app](mon.md)
