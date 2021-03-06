![1](https://user-images.githubusercontent.com/66811679/85100946-929eba80-b1be-11ea-937b-f4e47281f563.png)
## Devops task 2:

A CI/CD Pipeline implementation, or Continuous Integration/Continuous Deployment, is the backbone of the modern DevOps environment. It bridges the gap between development and operations teams by automating the building, testing, and deployment of applications.Having vast applications of these devops tools integrations , SCM tools like Github , management tools like Jenkins and container tool like docker becomes the backbone of this pipeline of CI/CD to launch the applications within few clicks where all the internal works are done by these tools in the background. The main intention of this pipeline is to make this deployment as fast as possible wherein no human intervention occurs.

## Creation of Dockerfile: 
Using the dockefile concept I've built an images that has git and jenkins pre installed and starts the jenkins services as soon as the container is lauched using that image. I've pre-installed git to support the github plugin in the jenkins services.


![3](https://user-images.githubusercontent.com/66811679/85101522-d0501300-b1bf-11ea-9c35-fe40c9f8ac4e.PNG)

Now build the image and push it to the docker hub using the following commands

![4](https://user-images.githubusercontent.com/66811679/85101920-bf53d180-b1c0-11ea-81da-d281907a61e0.PNG)

Launching the container: With the docker image created , it is now up to make the docker commands run inside the container launched by using the above image created so that Jenkins can directly launch the required containers. For this I've directly mounted the "docker.sock file" on to the container and the docker config files on to the container to make the docker commadns executable. Also expose the container on the port 8080 to access the WebUI of the Jenkins.

![6](https://user-images.githubusercontent.com/66811679/85104029-fc21c780-b1c4-11ea-9fb9-eb0abe135d19.PNG)

Jenkins running on the port number 8080,  enter the jenkins and  install the GITHUB plugin adn the build pipeline plugin.

## Screenshot 
## installed jenkins plugins


![7](https://user-images.githubusercontent.com/66811679/85106273-29707480-b1c9-11ea-97a1-bc40ab8d5e05.PNG)


![8](https://user-images.githubusercontent.com/66811679/85106312-3b521780-b1c9-11ea-94ff-fe0666bd58c7.PNG)

![9](https://user-images.githubusercontent.com/66811679/85106317-3f7e3500-b1c9-11ea-911d-54f08cfced56.PNG)


![10](https://user-images.githubusercontent.com/66811679/85106334-46a54300-b1c9-11ea-82e8-35a350728404.PNG)

![11](https://user-images.githubusercontent.com/66811679/85106378-5ae94000-b1c9-11ea-9846-23c13fb217f0.PNG)

![12](https://user-images.githubusercontent.com/66811679/85106393-5d4b9a00-b1c9-11ea-92bb-bbaae83c56fd.PNG)

![13](https://user-images.githubusercontent.com/66811679/85106399-5fadf400-b1c9-11ea-83b5-c2838f85e644.PNG)

![14](https://user-images.githubusercontent.com/66811679/85106413-63417b00-b1c9-11ea-887f-f99d1976a520.PNG)

![16](https://user-images.githubusercontent.com/66811679/85106420-65a3d500-b1c9-11ea-9543-2dbec9a0035c.PNG)


Moving furthur into various jobs of the jenkins. I've created a jenkins pipeline of 4 jobs wherein:

## JOB 1 : 
Pulls the code from github and copies it in the folder named code in the /var folder of the base container named "jen1" in my case. Ive used a remote URL trigger to trigger the job as soon as the code is launched to github by placing it in the post-commit actions of the git.

![19](https://user-images.githubusercontent.com/66811679/85107770-bfa59a00-b1cb-11ea-968f-89cac9f7d3a7.PNG)


![18](https://user-images.githubusercontent.com/66811679/85107456-3bebad80-b1cb-11ea-8e9f-65935764ad4f.PNG)


![b](https://user-images.githubusercontent.com/66811679/85108518-1495e000-b1cd-11ea-889c-b28807c07eb0.PNG)

## JOB 2 : 
This job triggers as soon as the JOB1 is built successfully and this job checks the code and respectively launches the respective interpreter, copies the code to that interpreter container and deploys the code to the webserver.


![c](https://user-images.githubusercontent.com/66811679/85109922-5d4e9880-b1cf-11ea-8342-2e567db0e3e4.PNG)


## JOB 3 :
This JOB simultaneously triggers after the successful build of the job2 and this job checks the "http code" of the webserver i.e., this job ensure if the code is working properly on the wenserver if it has any error it sends a mail to the developer to recheck the code.

![e](https://user-images.githubusercontent.com/66811679/85111107-1eb9dd80-b1d1-11ea-9d02-efca2e429d13.PNG)


![o](https://user-images.githubusercontent.com/66811679/85112365-c4218100-b1d2-11ea-8dce-89b32d596735.PNG)



## JOB4 :
After all the above mentioned jobs are run successfully then this job triggers and keeps on checking whether the interpreter container is running and if in case the container stops it starts the container again. Finally it acts as a monitoring job to monitor the interpreter container.

![s](https://user-images.githubusercontent.com/66811679/85113373-6aba5180-b1d4-11ea-9d68-d0d5d78d3aad.PNG)

![ww](https://user-images.githubusercontent.com/66811679/85137408-66a32980-b1fe-11ea-8f2b-602e7f477b47.PNG)

With all the jobs successfully run and no errors in the code , the port 80 of my apache webserver shows this output which is the php code in my github:

![tt](https://user-images.githubusercontent.com/66811679/85116539-b53ecc80-b1da-11ea-854d-610a95fcfb0f.PNG)

Using the build pipeline plugin I've created a project overview of the jobs so that it would be easy to manage the jobs which looks like :


![WhatsApp Image 2020-06-19 at 3 40 21 AM (1)](https://user-images.githubusercontent.com/66811679/85122965-a65d1780-b1e4-11ea-8d44-45cc06031d98.jpeg)





