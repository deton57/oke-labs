Welcome to OKE - Rancher lab.

Our goal will be to get familiar with Kubernetes solution on Oracle cloud,
and Rancher, as an open source tool that can manage the Kubernetes. 


## Before you begin, here are some prerequisite: ##


1. before you being make sure you have Oracle OCI account.
Sign in page: https://www.oracle.com/cloud/sign-in.html
If you don't have a cloud account, you can create a free trial here: 
<URL>
  
```diff 
- These steps apply only if you are using your current OCI Account, and you are not under root compartment
- please make sure you have permissions for:

- 1a. Creating Virtual Cloud Network and Subnets.
- 1b. Creating Compute Instance + Shapes + Images permission.
- 1c. Creating OKE Cluster with all the permissions.
- 1d. Make sure your OKE has permissions to create Networks and Storage.

- Links for policy permissions:
```
[Link for Common policies](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Concepts/commonpolicies.htm)

[Link for OKE Policies](https://docs.cloud.oracle.com/en-us/iaas/Content/ContEng/Concepts/contengpolicyconfig.htm)


2. Mobaxterm installed 
3. Putty + Puttygen installed 




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
