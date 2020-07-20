## Welcome to Part 3 - Installing Wordpress deployment on OKE using Rancher ##
 
Now that we have Rancher installed, and an OKE cluster created, 
we can simplify the deployments of different apps/storage/services and more.. 

In this part we are going to install Wordpress, and see how simple it is.
let's get started. 

First thing we are going to do is to access our created cluster. 

![image]()

Now we see that we have different projects and namespaces on our system,
they are default as this is a new cluster and nothing is created. 

## Creating a project ##

Let's start by creating a new project. 
Click on the "Add Project" button. 

![image]()

Name it "wordpress", and click on the "Create" button.

![image]()

Now let's access the project from the top menu. 

![image]()

## Creating your first app ##

Next, navigate to "Apps" from the top menu.

![image]()

and click on "Launch" on the left side of the screen.

Rancher has a rich app catalog, that can be easily deployed on your Kubernetes cluster.
let's search for "wordpress" using the search bar on the right corner. 

![image]()

Once you've found it, let's click on it. 

![image]() 

In the following deployment you have 3 placeholders for password input,
let's input a password: **WPRancher321!** (you can use your own/auto-generated) 

![image]()

Scroll down, and click on the "Launch" button. 
This will take a few moments..

Congratulations!
you have deployed your first app on Rancher (in this lab, of course)

![image]()

Let's play around and see some features that Rancher offer us. 
First, let's click on the deployment on the word "wordpress". 

![image]()

## Discovering Rancher features ## 

In the next screen you will see endpoints you can access,
this is a website you have deployed by a few clicks. 
you can click on one of the endpoints to access your website:

![image]()

And this is your Wordpress website:

![image]()

The IP address you see, is a provisioned Load Balancer,
Kubernetes can provision a Load Balancer per each service/ingress. 





