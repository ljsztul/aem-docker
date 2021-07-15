# Creating AEM Author & Publish in Docker
* # Pre-Requisite
 - Files on the ~/aem-base_image 
 - You need license.properties
 - cq-quickstart-6.x.x.jar

* # Setup
* Created Base Image out of Ubuntu Image
* Created Dockerfile for Author & Publisher with respective configuration files
* Run `docker build -t aem-base-image .` in the ~/aem-base_image folder
* Run `docker-compose up` to create Docker containers running all the AEM instances together

Optional for run individually each AEM Server
* Run `docker build -t aem-author .` in the ~/aem-author folder
* Run `docker build -t aem-publish .` in the ~/aem-publish folder