# Kubernetes ![image](https://user-images.githubusercontent.com/89352211/142737603-a00b2530-e159-4d80-9636-b23cc0cb1ec1.png)

In this project we will use Kubernetes to deploy / manage to multiple servers.

1. Kubernetes Cluster in Microsoft’s Azure Kubernetes Service (AKS) : For two environments: Staging and Production.
2. Creating a Container Registry, for storing files.
3. CI \ CD process using "Azure DevOps Organizations"
4. The CI process contained: " Build and push an image to container registry "
5. The CD process contained for each enviroment ( Staging and Production )
5.1 Create imagePullSecret With secretArguments:

'--from-literal=COOKIE_ENCRYPT_PWD=$(COOKIE_ENCRYPT_PWD) --from-literal=HOST=$(HOST) --from-literal=PORT=$(PORT) --from-literal=NODE_ENV=$(NODE_ENV) --from-literal=HOST_URL=$(HOST_URL) --from-literal=OKTA_CLIENT_ID=$(OKTA_CLIENT_ID) --from-literal=OKTA_CLIENT_SECRET=$(OKTA_CLIENT_SECRET) --from-literal=OKTA_ORG_URL=$(OKTA_ORG_URL)  --from-literal=PGHOST=$(PGHOST) --from-literal=PGUSERNAME=$(PGUSERNAME) --from-literal=PGDATABASE=$(PGDATABASE) --from-literal=PGPASSWORD=$(PGPASSWORD)  --from-literal=PGPORT=$(PGPORT)'

6. Deploy to Kubernetes cluster:
                $(Pipeline.Workspace)/manifests/deployment.yml
                $(Pipeline.Workspace)/manifests/service.yml
                $(Pipeline.Workspace)/manifests/ingress.yml
                
7. Kubectl Apply to deployment.yml



# Running Conditions At Work:

The variables are encrypted in the Library

There Are Two Brunches:
Main
Worker

Run Conditions:
* Worker Can Only Run Staging Provided That Build Has Passed Successfully.
* Main Can Also Run Staging And Production Provided That Build And Staging Are Successful



# Dockerfile contains:
* Create an app folder that contains the app files
* App installation and dependencies
* Expose to Port 80
* CMD: npm run Initdb + Dev


# NodeWeightTracker application on AKS meeting the following requirements:

* The NodeWeightTracker app is accessible from the Internet
* The NodeWeightTracker app is exposed to the Internet at port 80
* NodeWeightTracker is at least 3 instances to ensure high availability
* Configuration secrets to store your application configurations
* Expose your application using the ingress controller

# application lifecycle is automated with a CI/CD process
![image](https://user-images.githubusercontent.com/89352211/142738974-e66bbc94-3d1f-44ca-a6ab-7a8dbdcb775f.png)

# Project structure
![image](https://user-images.githubusercontent.com/89352211/142737633-c7e2a8fb-956d-489d-bafa-8886fecfa515.png)
![image](https://user-images.githubusercontent.com/89352211/142737732-ec01d94f-384e-4405-b6c4-7b2cb4be5b56.png)


# Pipelines Structure

![image](https://user-images.githubusercontent.com/89352211/142737788-acb7909c-63da-4cf1-9ed0-e71e22a3ad5e.png)


# Node.js Weight Tracker

![Demo](docs/build-weight-tracker-app-demo.gif)

