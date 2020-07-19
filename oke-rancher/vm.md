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

<image> 
  
Open the side menu, and go to Networking.

<image> 
  
Click on Virtual Cloud Networks.

<image> 
  
Click on Create VCN button.

1. Enter the name: "oke-rancher-lab"
2. Choose your compartment name.
3. CIDR BLOCK - you can choose every private subnet you with. 
example: "10.0.0.0/16"
* Make sure it's not overlapping with other subnets you have 
4. Click on Create VCN button on the buttom.

<image> 
  
Now click on the Create Subnet button.
1. Enter the name: "dev-subnet"
2. Leave the Regional option selected
3. from the CIDR BLOCK choose a sub-network from the choosen subnet previously. 
example: "10.0.0.0/24" 
4. Subnet access - must remain public (don't worry, we are just playing around). 
5. Scroll buttom and click on Create Subnet button.

<image> 
  
Congratulations! you now have created a Virtual Network + Subnet.
Let's continue to the second step.

<image> 
 
Step 2: 

## Add rules to security list ## 

Open the side menu, and go to Networking.

<image> 
  
Go to Virtual Cloud Networks. 

Choose your Virtual Cloud Network, you created previously. 

<image> 
  

Now navigate to Security Lists.

<image>

Click on the default security list. 

Click on Add Ingress Rule. 

Now we are going to add HTTPS access to our network, 
so we can access the web page of Rancher. 

1. Source CIDR input: "0.0.0.0/0" (I know it's not secured, never recommend you to do it. but it's for lab purpose)
2. DESTINATION PORT RANGE: "443" 
3. Click on Add Ingress Rule button.

<image> 
  

We finished step 2, now we have access to port 443. 

<image> 

  
 
Step 3: 

## Create a virtual machine and install Rancher ##

Open the side menu, and go to Compute.

<image> 
  
Click on the Create Instance button.

<image> 
  
1. Enter the name: "dev-oke-rancher"
2. Choose your compartment name.
3. Click on Change image, then Oracle images, look for Oracle 
"Oracle Cloud Developer Image"	
Scroll down and check the checkbox:
I have reviewed and accept the Oracle Standard Terms and Restrictions.
Click on Select Image. 
4.* Note you are going to create a shape with 1 OCPU (Intel) + 15Gb RAM.
5. Choose your Virtual Cloud Network you created before.
6. Choose your subnet you created before. 
7. Make sure that ASSIGN A PUBLIC IP ADDRESS is checked.

<image> 
  
8. Scroll down to Add SSH Keys. 

Here it's a bit tricky, but we will do it together. 

*****************
*****************
Add steps

<image> 
9. Click on Create 

<image> 
  

  
 
