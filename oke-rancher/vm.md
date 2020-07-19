## Welcome to part 1 - Creating the Rancher ## 
This will be the first step in our lab.
Our task is to create a virtual machine, 
with everything we need in order to create a Kubernetes cluster. 

In this section we will focus on 3 steps we need to create.
1. Virtual Cloud Network + Subnet for the virtual machine 
2. Add HTTPS/443 rule to the security list, in order to connect to Rancher. 
3. Virtual machine with Oracle Developer image, in order to create a Docker.  


Step 1: 

## Create a Virtual Cloud Network + Subnet ## 
After you are connected to your cloud account, 
you will see the following dashboard screen.


Open the side menu, and go to Networking.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/menu-networking.PNG)
    

Click on Virtual Cloud Networks.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/create-vcn.PNG)
  
Click on Create VCN button.

1. Enter the name: "oke-rancher-lab"
2. Choose your compartment name.
3. CIDR BLOCK - you can choose every private subnet you with. 
example: "10.0.0.0/16"
* Make sure it's not overlapping with other subnets you have 
4. Click on Create VCN button on the buttom.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/create-vcn2.PNG)  

Done. your VCN is created.


Now click on the Create Subnet button.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/create-subnet2.PNG)  

1. Enter the name: "dev-subnet"
2. Leave the Regional option selected
3. from the CIDR BLOCK choose a sub-network from the choosen subnet previously. 
example: "10.0.0.0/24" 
4. Subnet access - must remain public (don't worry, we are just playing around). 
5. Scroll buttom and click on Create Subnet button.


Congratulations! you now have created a Virtual Network + Subnet.
Let's continue to the second step.
 
Step 2: 

## Add rules to security list ## 

Open the side menu, and go to Networking.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/menu-networking.PNG)
  
Go to Virtual Cloud Networks. 

Choose your Virtual Cloud Network, you created previously. 
  
Now navigate to Security Lists.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/security-list.PNG)

Click on the default security list. 

Click on Add Ingress Rule. 

Now we are going to add HTTPS access to our network, 
so we can access the web page of Rancher. 

1. Source CIDR input: "0.0.0.0/0" (I know it's not secured, never recommend you to do it. but it's for lab purpose)
2. DESTINATION PORT RANGE: "443" 
3. Click on Add Ingress Rule button.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/security-list2.PNG)

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/security-list-result.PNG)  

We finished step 2!
now we have access to port 443. 


Step 3: 

## Create a virtual machine and install Rancher ##

Open the side menu, and go to Compute.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/menu-compute.PNG)  
  
Click on the Create Instance button.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/create-instance1.PNG)

1. Enter the name: "dev-oke-rancher"
2. Choose your compartment name.
3. Click on Change image, then Oracle images, look for Oracle 
"Oracle Cloud Developer Image"	
Scroll down and check the checkbox:

I have reviewed and accept the Oracle Standard Terms and Restrictions.

Click on Select Image. 

4.**Note you are going to create a shape with 1 OCPU (Intel) + 15Gb RAM.**

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/create-instance1.PNG)


5. Choose your Virtual Cloud Network you created before.
6. Choose your subnet you created before. 
7. Make sure that ASSIGN A PUBLIC IP ADDRESS is checked.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/create-instance2.PNG)


8. Scroll down to Add SSH Keys. 

Here it's a bit tricky, 
but we will do it together. 

1. Open putty keygen
![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/putty-keygen1.PNG)

2. click on generate button. 
and move your mouse a few times on the screen so a key will be generated. 

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/putty-keygen2.PNG)

3. **Important** Save the private key on your PC (click save private key)

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/putty-keygen3.PNG)

4. Save your public key content on your PC (copy the public key content from the screen and save it to notepad)

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/putty-keygen4.PNG)

Now, once we finshed, we can paste the public key into the SSH-KEY in OCI: 
 
![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/create-instance3.PNG)
 
9. Click on Create 
10. Let's wait 1~2 minutes until the Instance is provisioned, 
copy the public IP address and put it in a notepad.

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/public-ip.PNG)  
  
Now it's time to connect and install Rancher.
Because you have selected the Oracle Developer Cloud Image,
you don't need to install docker or any other tools for now.

Open your mobaxterm or other terminal. 
I will put here the steps for Mobaxterm, 
in putty you can use other steps (not written here)

1. Click Session
2. SSH
3. in the remote host enter your instance **Public IP** from where you saved it. 
4. specify username: opc 
5. Click on Advanced SSH Settings 
6. Check the use private key and load it from your directory. 

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/session-moba.PNG)
  
If you have succesfully followed the previous steps,
you can connect to the machine from the left side panel, by clicking twice on the machine name.

Once you are connected you should see the following output:

[opc@dev-machine ~]$

In order to create the Rancher on Docker, 
run the following command:

``sudo docker run -d --restart=unless-stopped \
  -p 80:80 -p 443:443 \
  rancher/rancher:latest``

Let's wait 1~2 minutes until the docker images are downloaded and the docker is up. 

run the following command: 

``sudo docker ps``

You should see something like this: 

90c3ff917b57        rancher/rancher:latest   "entrypoint.sh"     2 hours ago         Up 2 hours          0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp   focused_beaver

if you got this output, you rock! 
We just finished creating our Rancher,
let's continue to our next step. 

Click here to go to part 2: 

[Create an OKE cluster using Rancher](cluster.md) 


If you want to return to the lab homepage, click here:
[Back to the general lab section](readme.md)




  
 
