# Net-Core
Doing some .Net Core stuff

## Run this application
- Download and install .Net Core: https://www.microsoft.com/net/download/core
- Open Visual Studio Installer and add ".NET Core cross-platform development",
	you can follow instrutions on https://www.microsoft.com/net/core#windowsvs2017
- Install Docker for Windows ("Stable channel") https://docs.docker.com/docker-for-windows/install/ Restart computer after
- Try some commands to see Docker is properly installed: https://docs.docker.com/docker-for-windows/#check-versions-of-docker-engine-compose-and-machine
- Run this application from Visual Studio (Ctrl+F5)

# How I deployed application to Docker Hub and further to Azure:
"An **image** is a lightweight, stand-alone, executable package that includes everything needed to run a piece of software, including the code, a runtime, libraries, environment variables, and config files.

A **container** is a runtime instance of an image".

A **Dockerfile** will define what goes on in the environment inside your container.

- With help from this post: https://damienbod.com/2017/01/21/creating-an-asp-net-core-docker-application-and-deploying-to-azure/
- Do a Release-build of the application
- Open up the console and create a docker tag for the application.
	"docker tag persylnetcorewebapp persyl/mynetcorewebapp"
- Now login to docker hub in the command line:
	"docker login"
- Once logged in, the image can be pushed to docker hub
	"docker push persyl/mynetcorewebapp"
- Once deployed, you can view this on docker hub: https://hub.docker.com/u/persyl/

## Release Docker Hub image to Azure:
- Login to Azure Portal and select the + New and search for "Web App On Linux"
- Now configure the docker container by adding the newly created image on Docker Hub to the text field "persyl/mynetcorewebapp"
- Click create and the application will be deployed on Azure
- Now the application can be viewed on http://persylnetcore.azurewebsites.net

## Useful Docker commands
- "docker ps" List all running Docker processes
- "docker container ls -a" list all containers, also the not running ones
- "docker rm NAME" Remove a container where NAME is the name of the container
- "docker images" List all images
- "docker rmi NAME" Remove an image where NAME is the name of the image
- To remove untagged images, first run "docker images -f "dangling=true" -q" to get ID then use that ID in "docker rmi ID"
