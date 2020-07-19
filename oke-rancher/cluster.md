## Welcome to part 2 ##

In this part of the lab,
we are going to create the OKE cluster using the Rancher we created.

If you have completed the previous part successfully, you should be able to open 
the Rancher from your web browser. entering: 

https://{{public-ip}}:433
  
The public IP should be saved in a notepad.
**If you don't remember, follow these steps**
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

* OCI Console Account
* On the second one Rancher
* Mobaxterm terminal 



Let's start.

1. On your Rancher click on the "Add Cluster" 

<image>
  
2. Choose OKE Driver

<image>
  
  
3. Name the cluster "rancher-oke"

<image> 

4. Under Region: select your cloud region. 
If you look on OCI Console should be on the upper part.
Select the same in the Rancher cluster configuration screen. 


<image> 
  

4. Now we are going to use Mobaxterm terminal, 
We need to create a Public/Private key for the API, 
this is a different requirment than we did before.

you can open it and connect to your dev machine. 
command line/saved session
ssh opc@{{public-ip}} -i private.key 

Once your'e in, run the following commands: 

opc@dev-machine-87165 ~]$ 
```ssh-keygen -t rsa -b 4096 -m PEM -f $HOME/id_rsa```
## promt enter twice ## 

Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/opc/id_rsa.
Your public key has been saved in /home/opc/id_rsa.pub.
The key fingerprint is:
SHA256:aXgNRwwd/t0BGFE0hgHcT1jrW4m4YDgYM/gt8a581b4 opc@dev-machine-87165
The key's randomart image is:
+---[RSA 4096]----+
|        o===@B   |
|    .    +o=..+  |
|   . =  . o o. . |
|    . O..= .oo..o|
|     +.=Soo..o.o.|
|      ooo.... o  |
|       .. .. .   |
|    . ..   .     |
|     o.    E.    |
+----[SHA256]-----+

Now RSA Key generated. 
next step is to create the public key in PEM format. 

Run the following command: 

```openssl rsa -in id_rsa -pubout -out id_rsa_pub.pem```

Next command will be used in order to copy the content: 

```cat id_rsa_pub.pem```

Should be something like this:

``` 
-----BEGIN PUBLIC KEY-----
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAyQmFA7Kdx/DeN6qbg7ho
/7Yb2X+wAhzcyB4x3+IrU4r49mUoKtFrNoKHRSYsAt7Ofch74BdQ+UTRXhm+64ux
aJRQsvupEWcUC4CEQn+l6bNicskxl3LfpjxFaYVFWIWNo2Uk1O9STQ96gdFdh0xV
8HNPiWI7WNceVdlBhEw1FRFC3cZNec3jqV7YQvG8tL9pxSFTR/5hl0YWRfW2j5PK
tLstw1DWLcfjCpG7PHJ1Bm0q2JwYom5/L8G3EcCiEdqUJoJBSGqRV4O+fwv1fG6Z
YD8dZQ9FKhXlV0tLIBJ/3BPaqfrmteFojrGN4i3JAAtxP1O4Ok1qKKPcPt8z5GKS
nWHwzVorDUb0i5sQRCG13E3LRon4Qf0s4DTWUxVZ5N1AR1wtdcbxKAjwMBD/Hj5O
VfuPamh8Zjfxoz4RXNQCUklSYX1PU7413tyfKX2wP2V7g6CsonX5l0VWc/PdMgKc
ViBhD7bjQD6ujcSocNRNYAwUmPEqQHx4eDmRgNremNZhVg811FuQrbIsYpMAGEow
VmBuSxEsY76AWjFEfowmvkRaBad3F9LRFqVAkQ1d4NEZXTqRMNXsMrzSfFPj39IC
smPokzabZ0RQp+spak0p+IFYDW9kdhWqxBC2pI2ZPni5tP/h4yoRyeE0X1J4ewAr
00dRVxBiYfty4xpKjWMBgkUCAwEAAQ==
-----END PUBLIC KEY----- 
``` 

Copy the whole key, and minimize the Mobaxterm window (we will need it later). 

5. Open OCI Console 
Click on the top right corner on the profile,
and then click on your account name. 
<image>
  
On the left corner, click on API Keys.
<image>

Click on Create API Key

<image> 
 
paste the content from your machine generated key.

<image> 

You will notice that a fingerprint is created. 
copy the full fingerprint. 

<image> 


6. Go to the Rancher screen 
put the fingerprint under "user fingerprint" 

7. Go back to OCI console screen, on the same page you have OCID.
Copy your user OCID and paste in the Rancher screen under
"User OCID"

<image> 
<image> 

8. Open again your Mobaxterm 
run the following command: 
```cat id_rsa```

This will show your private key content,
copy it fully, without spaces. 
and paste it in the Rancher window under
"User Private Key"

<image>
 
9. Go to OCI Console 
click on the user profile icon
and select your tenancy
copy the Tenancy OCID and paste it into the Rancher cluster configuration screen.
"Tenancy OCID"

<image>



10. Last parameters step, go again to OCI Console 
Scroll down the left menu, click on identity. 

<image> 

and then on compartments, choose your compartment. 
copy the OCID of your compartment to Rancher cluster configuration screen.
"Compartment OCID"

11. Once all parameters configured, click on the button that says:
"Next Authenticate..." 

12. Leave the parameters as is, with 1 node per AD.
This will tell Rancher to create the OKE cluster with 1 node per AD, which result total of 3 nodes,
if you are running on a region with 3 ADs. 

13. Click "Next Virtual Cloud Network"
Choose the "Quick Create" 

14. Click "Next Configure Node Instances"
Choose the following 
shape: VM Standard2.1
Operating system: Oracle Linux 7.6

* Optional - you can paste your public key for the machine, the first one you created.
but this is not a must, only if you want to connect to one of the nodes. 

Final result

<image> 
  
Finally you can click on "Create" 

<image> 

If you done all the steps correctly and accurately, 
the cluster should be created, and congratulations! 
We finished part 2. 



