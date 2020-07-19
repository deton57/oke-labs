## Welcome to part 2 ##

In this part of the lab,
we are going to create the OKE cluster using the Rancher we created.

If you have completed the previous part successfully, you should be able to open 
the Rancher from your web browser. entering: 

https://{{public-ip}}:433
  
The public IP should be saved in a notepad.
**IF you don't remember, follow these steps**
1. Login to OCI Console
2. Go to Compute > Instances
3. Select the dev machine and copy the public address. 

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/public-ip.PNG)


In your browser, go to: 
https://{{public-ip}}:433
  

If you enter using Google Chrome as your browser, 
click on Advanced, and then click on the proceed link below:

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/rancher-home-sec.PNG)

In the next screen, you can set a password, 
in this lab I use: OKERancher123!
but you are not limited and you can set your own password.
After you set the password, check the checkbox that "Agree to the Terms"
and click continue.
![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/rancher-login.PNG)

On the next screen click on the button
"Save URL"

And you're in, you can see the Rancher dashboard! 


## Activate the OKE Driver ##

The OKE Driver, allows Rancher to work with OCI-OKE API
and to create and manage the cluster on Oracle.

1. Click on tools menu and select Drivers:

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/Rancher-Drivers.PNG)

2. Activate the OKE Driver

![image](https://github.com/deton57/oke-labs/blob/master/oke-rancher/screenshots/rancher-OKE-driver.PNG)

Wait a few seconds, once it's Active. 
We are almost ready. 

## Creating the cluster ## 

Now we are a step away from creating the cluster,
And here it will be a bit challanging, 
because we will need to prepare Rancher,
to work with our OCI Account.

We have one step to do, before staring.
We need to create an API key in our OCI Account. 

I suggest to open 3 screens 2 of Web Browser and 1 screen of Mobaxterm

1. OCI Console Account
2. On the second one Rancher
3. Mobaxterm terminal 




