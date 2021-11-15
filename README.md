# CI_CD - Docker![image](https://user-images.githubusercontent.com/89352211/141610015-3ee2d3f1-3975-4970-b979-b9dcfaafb1dd.png)

In this project, the Weight Tracker app was deployed using Docker.

Dockerfile contains:
* Create an app folder that contains the app files
* App installation and dependencies
* Expose to Port 8080
* CMD: npm run Initdb + Dev

# Project structure
![image](https://user-images.githubusercontent.com/89352211/141610155-bf94633b-1ee7-40ea-b125-8321ad5dbbce.png)
![image](https://user-images.githubusercontent.com/89352211/141610161-15d4ae89-f785-4d99-bf06-ff324c4daf93.png)
![image](https://user-images.githubusercontent.com/89352211/141610165-b2931763-a405-4547-87ed-595f5896f33f.png)


# Pipelines Structure
* Triggers: Main / worker
* Build CI: Build and push an image to container registry
* Build a Staging/Production CD:
Receive a set of variables using group variables that are connected to a vault key, at the most secure level.
2. Stop Current Container
3. Login to Registry
4. Download Azure Key Vault secrets
5. Delete folders, or files matching a pattern "variablesStaging/Production.env"
6. create a file: "variablesStaging/Production.env" which contains the set of variables secured in: BinariesDirectory.:

               6.1 PGHOST=$(PGHOSTP)
               6.2 PGUSERNAME=$(PGUSERNAMEP)
               6.3 PGDATABASE=$(PGDATABASEP)
               6.4 PGPASSWORD=$(PGPASSWORDP)
               6.5 PGPORT=$(PGPORTP)
               6.6 HOST_URL=$(HOSTURLP)
               6.7  COOKIE_ENCRYPT_PWD=$(COOKIEENCRYPTPWDP)
               6.8  NODE_ENV=$(NODEENVP)
               6.9  OKTA_ORG_URL=$(OKTAORGURLP)
               6.10  OKTA_CLIENT_ID=$(OKTACLIENTIDP)
               6.11  OKTA_CLIENT_SECRET=$(OKTACLIENTSECRETP)
               
8. Run New Container:
"docker run --restart = always -d --name weekdocker -p 8080: 8080 --env-file $ (Build.BinariesDirectory) /variablesST/PR.env $ (containerRegistry) / $ (imageRepository): $ (tag)"


# Terms of the Environments and the project:

* Dockerfile to package the NodeWeightTracker application into an image.
* Branch policies to force code review and build validation configured for the master/main branch
* CI/CD pipeline to automate the application lifecycle
* Images stored on Azure Container Registry (ACR)
 ![image](https://user-images.githubusercontent.com/89352211/141610776-ed6556ae-aa44-4ce3-af20-2ee9d674e929.png)



# Node.js Weight Tracker

![Demo](docs/build-weight-tracker-app-demo.gif)

