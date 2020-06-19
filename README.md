![1](https://user-images.githubusercontent.com/66811679/85100946-929eba80-b1be-11ea-937b-f4e47281f563.png)

A CI/CD Pipeline implementation, or Continuous Integration/Continuous Deployment, is the backbone of the modern DevOps environment. It bridges the gap between development and operations teams by automating the building, testing, and deployment of applications.Having vast applications of these devops tools integrations , SCM tools like Github , management tools like Jenkins and container tool like docker becomes the backbone of this pipeline of CI/CD to launch the applications within few clicks where all the internal works are done by these tools in the background. The main intention of this pipeline is to make this deployment as fast as possible wherein no human intervention occurs.

## Creation of Dockerfile: 
Using the dockefile concept I've built an images that has git and jenkins pre installed and starts the jenkins services as soon as the container is lauched using that image. I've pre-installed git to support the github plugin in the jenkins services.


![3](https://user-images.githubusercontent.com/66811679/85101522-d0501300-b1bf-11ea-9c35-fe40c9f8ac4e.PNG)

Now build the image and push it to the docker hub using the following commands

![4](https://user-images.githubusercontent.com/66811679/85101920-bf53d180-b1c0-11ea-81da-d281907a61e0.PNG)

Launching the container: With the docker image created , it is now up to make the docker commands run inside the container launched by using the above image created so that Jenkins can directly launch the required containers. For this I've directly mounted the "docker.sock file" on to the container and the docker config files on to the container to make the docker commadns executable. Also expose the container on the port 8080 to access the WebUI of the Jenkins.

![5](https://user-images.githubusercontent.com/66811679/85102355-b7486180-b1c1-11ea-823b-23cbeb77bb41.PNG)

Jenkins running on the port number 8080,  enter the jenkins and  install the GITHUB plugin adn the build pipeline plugin.

