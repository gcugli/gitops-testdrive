# Deploying a simple application on Cluster

The application to deploy is PetClinic, this application is stored now in your GIT repo on the "petclinic-app/02-petclinic" path.

The goal in this section is navigate and deploy this applicaction on the cluster.

# Start ArgoCD Console

For this excercise, every user has his own ArgoCD server already deployed in a namespace called "userXY-openshift-gitops". In order to access to the ArgoCD web console and login, go to Developer view > Select Topology from the left menu > Then select the Project "userXY-openshift-gitops"

![Deploying Application](../img/installingC66.png "Deploying Application")

Now click in the arrow next to the POD called "argo-server" to open the URL.

![Deploying Application](../img/installingC67.png "Deploying Application")

If your browser shows a security conection issue, please accept and proceed with the URL (we install ArgoCD with a self-signed certificate).

![Deploying Application](../img/installingC68.png "Deploying Application")


The ArgoCD web console will be open now. 

![Deploying Application](../img/installingC77.png "Deploying Application")


We are going to access with the ArgoCD "admin" user in order to get all the features that ArgoCD offers. So first we need to obtain the default "admin" password. In order to do so, go to the Openshift Web Console > then "Developer View" > then select "Secrets" from the left menu:

![Deploying Application](../img/installingC78.png "Deploying Application")

Click in the "argocd-initial-admin-secret" secret and look at the "Data" section. There is a key with name "password" and has a hidden value. Click in "Reveal values" link in order to reveal the password. Then take note of this password.

![Deploying Application](../img/installingC79.png "Deploying Application")


Return to the ArgoCD's login page and login with the "admin" user and enter the password. Verify that has access to ArgoCD console

![Deploying Application](../img/installingD3.png "Deploying Application")

Create a new application

![Deploying Application](../img/deployappsA1.png "Deploying Application")

Write the follow data in General section:

* Application name: petclinic
* Project: default
* Sync Policy: Manual

![Deploying Application](../img/deployappsA2.png "Deploying Application")

Complete the source and destination

*Source*

* Repository URL: [your-git-repo-url]/gitops-testdrive
* Revision: HEAD
* Path: petclinic-app/02-petclinic

Example with GitHub: https://github.com/[your-username]/gitops-testdrive

*Destination*

* Cluster URL: https://kubernetes.default.svc
* Namespace: petclinic

![Deploying Application](../img/deployappsA3.png "Deploying Application")

Finally, maintain the values of Kustomize as the image

![Deploying Application](../img/deployappsA4.png "Deploying Application")


Select **Create** in the top of screen and wait to application Syncronize

![Deploying Application](../img/deployappsA4.png "Deploying Application")

The application is present on the main ArgoCD Main Screen

![Deploying Application](../img/deployappsA5.png "Deploying Application")

Select Sync over the petclinc application and confirm default options

![Deploying Application](../img/deployappsA7.png "Deploying Application")

When the application is syncronized, go to OpenShift and explore the application

![Deploying Application](../img/deployappsA8.png "Deploying Application")

On OpenShift go to Developer perspective and identify all objects created

* What objects was created?
* Where is located the application?
* What is the application objective?

[Go to content](content.md)
[Go to readme](../README.md)
