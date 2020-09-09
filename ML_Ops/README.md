# ML Model Building and Deployment
## Installation and Configration
### Environment-Setup Virtual Box
* Download & Install virtual Box from given link based upon your operating system. [https://www.virtualbox.org/wiki/Downloads]
* After installation of virtual box, download ubuntu image or any Linux flavor. For ubuntu click to: [https://ubuntu.com/download/desktop/thankyou?version=18.04.3&architecture=amd64]
* Click New -> <Give Name to OS> like Linux -> <Give Memory size or set it default to 1 GB> -> Click Create -> Next -> Next -> Give the file storage size set it to at least 20 GB -> click Create .
* Locate the .iso image you saved and go to network and select drop down Attached to with bridge adapter and name to your wireless adapter (choose the wifi connector).
* And now click OK and start your Virtual machine click Install ubuntu -> follow the procedure of installation. Make everything default if it’s your first installation and new to every setting and click next while installing because this is VM and our host OS would remain unaffected.
* Connect your system to internet and start your ubuntu VM.
* After successfully installation open ubuntu VM and open terminal. [ Type -> ifconfig ] If it doesn’t run the you have to fire these commands and check [ifconfig] again:
```
sudo apt-get update
sudo apt install net-tools
```
* Check whether first two address of IP address of your host and vm is same or not e.g 192.148.xx.xx. If not run the following command and restart the VM
```
sudo apt update
sudo apt install openssh-server
```
* Above command is for connection with ssh to your local system via putty, cmd or powershell.
* Now install and open putty and type your ubuntu username and password. You will be connected to you VM. 

### Environment-Setup Docker
To install docker connect you system to internet. And on terminal give these commands:
* Step-01 : Update the apt package index: [sudo apt-get update]
* Step-02 : Install packages to allow apt to use a repository over HTTPS:
```
  sudo apt-get install \
       apt-transport-https \
       ca-certificates \
       curl \
       gnupg-agent \
       software-properties-common
```
* Step-03 : Add Docker’s official GPG key: [curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -]
* Step-04 : Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C0EBF CD88, by searching for the last 8 characters of the fingerprint.
  [sudo apt-key fingerprint 0EBFCD88]
* Step-05 : Use the following command to set up the stable repository.
```
sudo add-apt-repository \
"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) \
stable"

```
* Step-06 : Update again [sudo apt-get update]
* Step-07 : Install the latest version of Docker Engine – Community [sudo apt-get install docker-ce docker-ce-cli containerd.io]
* Step-08 : To check the installation is successful run [sudo docker run hello-world]

### Environment-Setup Jenkins [How to install Jenkins on Ubuntu 18.04]
Jenkins is an open source Continuous Integration server capable of orchestrating a chain of actions that help to achieve the Continuous Integration process (and not only) in an automated fashion. Jenkins is free and is entirely written in Java. Jenkins is a widely used application around the world that has around 300k installations and growing
day by day.It is a server-based application and requires a web server like Apache Tomcat. The reason Jenkins became so popular is that of its monitoring of repeated tasks which arise during the development of a project. For example, if your team is developing a project, Jenkins will continuously test your project builds and show you the errors in early stages of your development.By using Jenkins, software companies can accelerate their software development process, as Jenkins can automate build and test at a rapid rate.
Jenkins supports the complete development lifecycle of software from building,testing, documenting the software, deploying and other stages of a software development lifecycle.
* Install Java [https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04#installing-specific-versions-of-openjdk]
* sudo add-apt-repository ppa:webupd8team/java
#### Add the Jenkins Repository
* Add the signing key for Jenkins Repository [wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -]
* To install stable releases of Jenkins, run the following command to add the stable repository. [sudo apt-add-repository "deb https://pkg.jenkins.io/debian-stable binary/"]
* To install the most recent releases, add the following repository instead. [sudo apt-add-repository "deb http://pkg.jenkins-ci.org/debian binary/"]
#### Install and Configure Jenkins
* Install Jenkins [sudo apt install jenkins]
* Get the root password automatically generated during the installation. [sudo cat /var/lib/jenkins/secrets/initialAdminPassword]
* When installed, open a web browser and navigate to your server using port 8080. Enter the root password in the input field.
* Jenkins is now installed and ready to use. [http://localhost:8080 or http://[VM_IP]:8080]
* https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-install-jenkins-on-ubuntu-18-04-bionic-beaver/

### Environment-Setup GitHub
To install GitLab open your Virtual box and your ubuntu VM. Connect it with you putty or you can run it on your ubuntu terminal as well.
GitLab is a web-based DevOps lifecycle tool that provides a Gitrepository manager providing wiki, issue-tracking and CI/CD pipeline features, using an open-source license, developed by GitLab Inc. The software was created by Ukrainians Dmitriy Zaporozhets and Valery Sizov, and is used by several large tech companies. Gitlab is a service that provides remote access to Git repositories. In addition to hosting your code, the services provide additional features designed to help manage the software development lifecycle. These additional features include managing the sharing of code between different people, bug tracking, wiki space and other tools for 'social coding'. 
* First pull the docker image, run-> [sudo docker pull gitlab/gitlab-ce] 
* Make sure you have at least 2 GB of data because Gitlab will be much heavy image to pull. 
* After successfully pulling image run-> [sudo docker run -d -p 443:443 -p 22:22 -p 80:80 --name Gitlab <Image name: tag or ImageID>]
  [sudo docker run -d -p 445:443 -p 2200:22 -p 90:80 --name Gitlab 0c78ed7cea0a]

### FLASK
Flask:Flask is a popular Python web framework, meaning it is a third-party Python library used for developing web applications. It is classified as a microframework because it does not require particular toolsor libraries. It has no database abstraction layer, form validation, or any other components where pre-existing third-party libraries provide common functions.However, Flask supports extensions that can add application features as if they were implemented in Flask itself. Extensions exist for object-relational mappers,form validation, upload handling, various open authentication technologies andseveral common framework related tools. Extensions are updated far more frequently than the core Flask program. 

## Natural Language Processing Programming

## Flask NLP Model

## Docker & DockerFile

## CICD Pipeline and Jenkins Configration



## Important Links
* https://towardsdatascience.com/rendezvous-architecture-for-data-science-in-production-79c4d48f12b
* Randomness: https://www.kdnuggets.com/2017/06/surprising-complexity-randomness.html
* Embrace Randomness in Machine Learning : https://machinelearningmastery.com/randomness-in-machine-learning/
* Apache Kafka to Drive Machine Learning https://www.confluent.io/blog/using-apache-kafka-drive-cutting-edge-machine-learning/
* Streaming Examples : https://github.com/kaiwaehner/kafka-streams-machine-learning-examples
* Deep Learning Spark: https://towardsdatascience.com/deep-learning-with-apache-spark-part-1-6d397c16abd
* MLFLOW : https://github.com/mlflow/mlflow
* https://github.com/ddotabma/rendezvous-on-aws
* https://github.com/SQLShark/MachineLearningFromModelToProduction
* https://medium.com/syncedreview/google-ai-chief-jeff-deans-ml-system-architecture-blueprint-a358e53c68a5
* https://christophergs.com/machine%20learning/2019/03/17/how-to-deploy-machine-learning-models/
