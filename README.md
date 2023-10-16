Project 1
Building a CI/CD Pipeline for a Retail Company
Name: Abhishek Kumar
Email: Abhishekkumar8811302@gmail.com
Phone: +91 7004609984
First of all, thanks very much to edureka and instructors for giving me confidence that Ican do any
type of devops projects. I just loved working on this project.
I have chosen project 1 out of two projects. So I implemented the 1st project.
github respository: https://github.com/Abhishek7884/finalproject
For validation:
please run this pipeline job in jenkins for task-3 deploying to tomcat and docker build and run
the container and uploading to dockerhub
CI_CD_DOCKER_V2
please run this pipeline job in jenkins for task-4 deploying to kubernetes and docker using
jenkins
CI_CD_PIPELINE_KUBERNETEES_V2/
Business Challenge/Requirement:
ABC Technologies is a leading online retail store, and it has recently acquired a large retail
offline business store. The business store has a large number of stores across the globe but
is following the conventional pattern of development and deployment. As a result, it has
landed at a great loss and is facing the following challenges.
● Low available
● Low scalable
● Low performance
● Hard to built and maintain •
● Developing and deploying are time-consuming
ABC will acquire the data from all these storage systems and plans to use it for analytics and
prediction of the firm’s growth and sales prospects. In the first phase, ABC has to create the
servlets to add a product and display product details. Add servlet dependencies required to
compile the servlets. Create an HTML page that will be used to add a product. The team is
using Git to keep all the source code.
ABC has decided to use the DevOps model. Once source code is available in GitHub, we
need to integrate it with Jenkins and provide continuous build generation for continuous
delivery as well as integrate with Ansible and Kubernetes for deployment. Use Docker Hub
to pull and push images between Ansible and Kubernetes.
Problem Statements/Tasks:
We need to develop a CI/CD pipeline to automate the software development, testing,
packaging, and deployment, reducing the time to market the app and ensuring good quality
service is experienced by end users. In this project, we need to—
● push the code to our GitHub repository.
● create a continuous integration pipeline using Jenkins to compile, test, and
package the code present in GitHub.
● Write Dockerfile to push the war file to the Tomcat server.
● Integrate Docker with Ansible and write the playbook.
● Deploy artifacts to the Kubernetes cluster • Monitor resources using Grafana.
Approach to Solve:
Task 1: Clone the project from the GitHub link shared in resources to your local machine.
Build the code using Maven commands.
Task 2: Set up the Git repository and push the source code. Then, log in to Jenkins.
1. Create a build pipeline containing a job for each
● One for compiling source code
● Second for testing source code
● Third for packing the code
2. Execute the CI/CD pipeline to execute the jobs created in step 1
3. Set up a master-slave node to distribute the tasks in the pipeline
Task 3: Write a Docket file. Create an Image and container on the Docker host. Integrate
docker host with Jenkins. Create CI/CD job on Jenkins to build and deploy on a container.
1. Enhance the package job created in step 1 of task 2 to create a docker image.
2. In the Docker image, add code to move the war file to the Tomcat server and build the
image.
Task 4: Integrate the Docker host with Ansible. Write an Ansible playbook to create an
image and create a continuer. Integrate Ansible with Jenkins. Deploy Ansible-playbook.
CI/CD job to build code on ansible and deploy it on docker container
1. Deploy Artifacts on Kubernetes
2. Write pod, service, and deployment manifest file
3. Integrate Kubernetes with Ansible
4. Ansible playbook to create deployment and service
Task 5: Using Prometheus, monitor the resources like CPU utilisation: Total Usage, Usage
per core, usage breakdown, memory, and network on the instance by providing the
endpoints on the local host. Install the node exporter and add the URL to the target in
Prometheus. Using this data, log in to Grafana and create a dashboard to show the metrics.
Let’s start…
Task 1: Clone the project from the GitHub link shared in resources to your local machine.
Build the code using Maven commands.
Approach i have followed:
- As a given project is based on java I have used maven as a build tool to build the code.
maven and java are installed already in the master machine. I have run the maven
compile,test,and package tasks successfully in the local environment and produced the
results for each and also executed the maven clean install command to build the code.
- Before this I have downloaded the sample Java code from the LMS into my own local
environment and used git bash to upload to the below newly created public github repository
and also i have uploaded all the code that i have developed to do this project in this
repository and all the important files are kept within the directory project_required_file_v2 of
project.
Repository: https://github.com/Abhishek7884/finalproject
- And executed the below tasks of maven in edureka local environment.
1. /opľ/maven/bin/mvn compile
2. /opľ/maven/bin/mvn ľesľ
3. /opľ/maven/bin/mvn package
4. /opľ/maven/bin/mvn clean insľall
- /opt/maven/bin/mvn - Is the path of the maven executable.
1) /opt/maven/bin/mvn compile: Compiles source code of the project
2) /opt/maven/bin/mvn test: Runs tests for the project.
3) /opt/maven/bin/mvn package: Creates WAR file for the project to convert it into a
distributable format.
4) /opt/maven/bin/mvn clean install: Using the clean command, which will delete all
previously compiled Java .class files and resources (like .properties) in the project. build will
start from a clean slate.
- Install will then compile, test & package my Java project and even install/copy my built
.war file into my local Maven repository.
- Below are the snapshots of results that I did in the edureka provided Lab terminal.
Compile task running in local:
Test task running in local:
Package task running in local:
History and target folder after the maven tasks completed
Classes folder contains compilation data and package task created .war
executable file to deploy.
References:
https://www.marcobehler.com/guides/mvn-clean-install-a-short-guide-to-maven
https://www.geeksforgeeks.org/maven-lifecycle-and-basic-maven-commands/#:~:text=mvn%
20compile%3A%20Compiles%20source%20code,it%20into%20a%20distributable%20forma
t.
Task 2: Set up the Git repository and push the source code. Then, log in to Jenkins.
2. Create a build pipeline containing a job for each
● One for compiling source code
● Second for testing source code
● Third for packing the code
2. Execute the CI/CD pipeline to execute the jobs created in step 1
3. Set up a master-slave node to distribute the tasks in the pipeline
Approach i have followed:
- Jenkins has been installed in master server already so i have created the 3 jobs for
compile,test,package in jenkins and created pipeline with these 3 jobs and set up the agent
machine(slave machine) and shared the load to agent as well.
- As a given project is based on java i have used maven to build the code and Jenkins is a
build automation server that helps to automate these things so i have set up the java,maven
paths of master in global tool configuration in jenkins and set up the jenkins goals and left git
path as default.
- Tools location :
/opt/maven
/usr/lib/jvm/java-8-oracle
- Goals:
compile
test
Package
Please find the screenshots of the above task-2:
Jenkins login:
Global tool configuration:
Tool location configuration for java:
Tool location configuration for git as default:
Tool configuration for maven:
Compile job result in jenkins:
Test job results in jenkins:
Package job result in jenkins:
Target folder in jenkins:
Step 2: Execute the CI/CD pipeline to execute the jobs created in step 1
CI_PIPELINE:
And I have configured the git polling as a cron job for a compile job that triggers for every 2
minutes for github code so that if whatever change happens then it will trigger and perform
the given task.
https://github.com/Abhishek7884/finalproject
Poll SCM settings using cronjob in compile job:
Step 3: Set up a master-slave node to distribute the tasks in the pipeline
The agent configurations:
- I have created a user jenkins on second linux machine so that i can run the jenkins jobs
in slave machine as well.
- When i try to configure the agent i was getting compatibility issue while running the agent
command in agent server(slave server) and got to know that this is due to java 8
compatibility issue beginning with Jenkins 2.357 and Jenkins 2.361.1, running the controller
on Java 11 and agents on Java 8 will result in the following error:
Error: A JNI error has occurred, please check your installation and try
again
Exception in thread "main" java.lang.UnsupportedClassVersionError:
hudson/remoting/Launcher has been compiled by a more recent version of
the Java Runtime (class file version 55.0), this version of the Java
Runtime only recognizes class file versions up to 52.0
at java.lang.ClassLoader.defineClass1(Native Method)
at java.lang.ClassLoader.defineClass(ClassLoader.java:756)
at
java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
at java.net.URLClassLoader.defineClass(URLClassLoader.java:473)
at java.net.URLClassLoader.access$100(URLClassLoader.java:74)
at java.net.URLClassLoader$1.run(URLClassLoader.java:369)
at java.net.URLClassLoader$1.run(URLClassLoader.java:363)
at java.security.AccessController.doPrivileged(Native Method)
at java.net.URLClassLoader.findClass(URLClassLoader.java:362)
at java.lang.ClassLoader.loadClass(ClassLoader.java:418)
at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:352)
at java.lang.ClassLoader.loadClass(ClassLoader.java:351)
at
sun.launcher.LauncherHelper.checkAndLoadMain(LauncherHelper.java:601)
So I installed the java 11 version in the agent machine and set up the environment variables
to make the java 11 as default version in both jenkins and agent machines.
exporľ JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
exporľ PATH=$JAVA_HOME/bin:$PATH
After upgrading the java8 version to java11 i am able to run the below agent commands in
agent machine and got connected to the agent from jenkins console and able to run the jobs
in agent machine and also configured the compile job to run this job only in agent machine.
I have created a /opt/jagenthome directory in the agent machine so that it will be used as a
working directory to put the result and I have set the jenkins url with the private ip of the
master node because if it is with the public ip it will always changes after every restart.
Agent commands that i run in agent machine:
> curl -sO http://172.32.10.56:8080/jnlpJars/agent.jar
> java -jar agent.jar -jnlpUrl http://172.32.10.56:8080/computer/agent01/jenkins-agent.jnlp
-secret bd3430016519c105e23863c50b9f01057092154668f863d217a035bbe7e79d2c
-workDir "/opt/jagenthome"
After running …
Agent connected validation in jenkins
Package job running in agent01 machine(example)
Making a compile job to run in agent01 machine only.
Agent01 build history
Note: I have modified the compile job again for the next set of tasks.
References:
https://www.jenkins.io/blog/2022/06/28/require-java-11/
https://www.jenkins.io/doc/administration/requirements/upgrade-java-guidelines/#:~:text=If%
20you're%20upgrading%20your,screen%20of%20your%20Jenkins%20instance.
https://stackoverflow.com/questions/69495517/unable-to-install-jenkins-on-ubuntu-20-04
https://stackoverflow.com/questions/14119983/java-home-and-path-are-set-but-java-versionstill-shows-the-old-one
Task 3: Write a Docket file. Create an Image and container on the Docker host. Integrate
docker host with Jenkins. Create CI/CD job on Jenkins to build and deploy on a container.
1. Enhance the package job created in step 1 of task 2 to create a docker image.
2. In the Docker image, add code to move the war file to the Tomcat server and build
the image
Approach i have followed:
- Jenkins and Docker are already installed in master machine and slave machine.
- Now using earlier jenkins package job with more enhancement with docker integration and
doing two things here
i) Deploying .war file generated from package job into the tomcat server
ii) And creating the docker build and docker container with above .war file
generated from package command and uploading the docker image to the docker hub and
running this docker image as container.
Step1: Deploying .war file generated from package job into the tomcat server
Issue 1:
And as part of Tomcat deployment I have tried to deploy using shell commands by copying
the .war file to the webapps/ folder but it did not work and I got the below error at that time.
Error message:
"sudo: no tty present and no askpass program specified
Build step 'Execute shell' marked build as failure
Finished: FAILURE"
I thought to copy the SSH public file to the slave machine but it not worked out. So finally I
followed a new way to deploy the .war file.
Solution:
Added the 'Deploy to container' plugin and modified the package_docker_v2 job and
configured the post-build action to deploy to the tomcat server.
Issue 2:
After running the job I got an issue and was not able to get into the tomcat so i have
configured the tomcat conf/tomcat-users.xml file with the below addition to the end like i
have created a user as a tomcat and password as a admin for the role of manager-gui and
manager_script and later it allowed me to deployed to the tomcat successfully.
Solution:
conf/ľomcaľ-users.xml
<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<user username="tomcat" password="admin" roles="manager-gui,manager-script"/>
Issue 3:
While running the build i got issue that jenkins not able to deploying to the tomcat and figure
out that whenever we restarted Lab tomcat will not start automatically so i have added one
more build stage as Execute shell to start the tomcat and also got error even after this
because tomcat will not initialize immediate start so i have included sleep 10 command as
well for it to initialize totally.
Solution:
> sudo bash /opt/tomcat/bin/startup.sh
> sleep 10
Step 2: Creating the docker build and docker container with above .war file
generated from package command and uploading the docker image to the
docker hub and running this docker image as container.
- As part of building docker images and uploading to dockerhub and running in the docker
container.
I tried to build the docker image manually in local and it got successful as part of that i have
created a Dockerfile and added the plugins "cloudbees docker build and publish",
“docker pipeline”, “docker plugin”,”docker build sľep”.
After installation of plugins you should be able to see the build/publish docker image in
the build section of jenkins job and one more option "docker build and publish" , if you see
that your plugin is installed successfully.
For telling jenkins to prepare docker image we need to build the DockerFile , now we need to
give instructions to jenkins but it will read this Dockerfile in the home directory so i have
placed this file in home directory and after build i have pushed the docker image to the
docker hub for that i need to give my docker hub credentials to jenkins so for giving
credentials i have configured the job in the build section "Docker build and publish" and
validated in local and docker hub after build the job.
And while running the job i get into the below issues
Issue 4:
Got permission denied while trying to connect to the Docker daemon socket at
unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.40/containers/json:
dial unix /var/run/docker.sock: connect: permission denied
Solution:
I have added the below commands in newly created build section Exceute shell before
starting to build the docker image
sudo chmod 666 /var/run/docker.sock
sudo chmod 777 /var/lib/jenkins/.docker/config.json
Sudo chmod 777 .docker
And also added the below additions in /etc/sudoers file(sudo file)
jenkins ALL=(ALL) NOPASSWD: ALL
Please find ľhe screenshoľs:
Issue 5:
jenkins.model.InvalidBuildsDir: ${ITEM_ROOTDIR}/builds does not exist and probably
cannot be created at jenkins.model.Jenkins.checkRawBuildsDir(Jenkins.java:3085) at
jenkins.model.Jenkins.loadConfig(Jenkins.java:3009) Caused: java.io.IOException
Solution:
experienced this when the $JENKINS_HOME/jobs directory had incorrect permissions or
ownership so provided the permissions for jenkins user for this jenkins home directory.
Issue 6:
While building docker image with Dockerfile it is not recognizing the .war file path that i
have mentioned in Dockerfile and got below error
((ADD /var/lib/jenkins/workspace/package_kubernetes2/target/ABCtechnologies-1.0.war
/usr/local/tomcat/webapps ADD failed: file not found in build context or excluded by
.dockerignore: stat
var/lib/jenkins/workspace/package_kubernetes2/target/ABCtechnologies-1.0.war))
Solution:
So i did modified the Dockerfile with the below changes **/*.war instead of target/*.war
Steps to configure the job for docker integration after installed above mentioned plugins
Create build tab with maven package and then ‘docker build and publish’ plugin added and
go to configure In build tab -> select ‘docker build and publish’ -> Repository
name(admin/abctechnologies) -> and add Registry credentials with ‘username and password’-
and that’s it it will get success.
Dockerfile
FROM docker.io/library/ubuntu:18.04
RUN apt-get -y update && apt-get -y upgrade
RUN apt-get -y install openjdk-8-jdk wget
RUN mkdir /usr/local/tomcat
ADD https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.68/bin/apache-tomcat-9.0.68.tar.gz
/tmp/apache-tomcat-9.0.68.tar.gz
RUN cd /tmp && tar xvfz apache-tomcat-9.0.68.tar.gz
RUN cp -Rv /tmp/apache-tomcat-9.0.68/* /usr/local/tomcat/
ADD **/*.war /usr/local/tomcat/webapps
EXPOSE 8080
CMD /usr/local/tomcat/bin/catalina.sh run
Below are the screenshots of the above 2 steps of task-3
Package_docker_v2 job settings
Git repo settings1
Git repo settings1
Choosing ‘Invoke top-level Maven targets’ option to add maven goal
Maven setting1
Giving permissions to the jenkins user by adding below commands in Exceute
shell in build step.
Docker plugins installed from manage plugins->available tab
Docker plugins installed successfully
‘Docker build and publish’ build step settings
Click on Add credentials and give user name and password for docker login
After setting above credentials selecting the credentials in ‘Registry
credentials’
After pushing the image to dockerhub starting the docker container
Before deploying to tomcat, I am starting the tomcat and waiting for sleep 10
seconds to initialize completely.
Selecting ‘Deploy war/ear to a container’ for tomcat settings
Tomcat settings1
Tomcat settings2
Tomcat validation1
Tomcat manager login
Tomcat manager UI that shows all the .war deployed files. We can deploy from
here as well.
Package job success
Docker hub push success message
Docker push and tomcat running success message
Validating in terminal for docker images
Validating container is running or not
Docker container validation in browser
Tomcat browser validation
Creating pipeline
Setting the upstream
Modifying the job configuration for pipeline connectivity
Before triggering pipeline view
Started pipeline
sLast job running in pipeline
Success run for pipeline
Validating in build and showing Test job as a downstream for compile job
Test results upstream details
Validating who is started the test job
Success log of pipeline last job(package_docker_v2)
Docker-hub validation after pushing from jenkins:
References i have followed:
https://plugins.jenkins.io/role-strategy/
https://stackoverflow.com/questions/37603621/jenkins-sudo-no-tty-present-and-no-askpassprogram-specified-with-nopasswd
https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.68/bin/apache-tomcat-9.0.68.tar.gz
https://phoenixnap.com/kb/how-to-configure-docker-in-jenkins
https://www.tutorialspoint.com/docker/docker_continuous_integration.htm
https://www.provartesting.com/documentation/devops/continuous-integration/docker/settingup-continuous-integration-with-jenkins-for-docker/
https://www.youtube.com/watch?v=mszE-OCI2V4&list=PLVz2XdJiJQxwS0BZUHX34ocLTJt
RGSQzN&index=4
https://www.digitalocean.com/community/questions/how-to-fix-docker-got-permission-denied
-while-trying-to-connect-to-the-docker-daemon-socket
https://stackoverflow.com/questions/50798720/jenkins-throwing-error-jenkins-model-invalidb
uildsdir-item-rootdir-builds-d
https://linuxize.com/post/how-to-list-groups-in-linux/
https://stackoverflow.com/questions/17733671/how-can-i-tell-what-user-jenkins-is-running-as
https://stackoverflow.com/questions/55156958/jenkins-fail-to-deploy-war-to-tomcat-container
-second-time
Task 4: Integrate the Docker host with Ansible. Write an Ansible playbook to create an
image and create a continuer. Integrate Ansible with Jenkins. Deploy Ansible-playbook.
CI/CD job to build code on ansible and deploy it on docker container.
1. Deploy Artifacts on Kubernetes
2. Write pod, service, and deployment manifest file
3. Integrate Kubernetes with Ansible
4. Ansible playbook to create deployment and service
Approach i have followed:
- The task-4 starting of integrating the jenkins with ansible. and creating the ansible playbook
integration of docker and then kubernetes.
- And this task is an extension of the last task so I have used the DockerFile I prepared in
the last task and added a few more steps.
- First of all i have configured the ansible hosts file with localhost and copied the self public
key to the master machine as jenkins needs authentication internally to connect to the
localhost(self) otherwise i will get authentication errors.
edureka lab has installed the required tools jenkins,ansible,docker,kubernetes
Kubernetes version:
Client Version: v1.18.3
Server Version: v1.18.20
Ansible version:
ansible 2.9.17
config file = /etc/ansible/ansible.cfg
configured module search path = [u'/home/edureka/.ansible/plugins/modules',
u'/usr/share/ansible/plugins/modules']
ansible python module location = /usr/lib/python2.7/dist-packages/ansible
executable location = /usr/bin/ansible
python version = 2.7.17 (default, Jul 20 2020, 15:37:01) [GCC 7.5.0]
So i have installed the ansible plugin in jenkins to run the playbook with provided
ansible-playbook and inventory file paths to run the ansible-playbook.
The ansible playbook created with docker module to build the image and then start the build
container with provided .war file path in Dockerfile. and i have used two docker modules
'community.docker.docker_image' and 'community.docker.docker_container'
to build the image and run the container.
the ansible-playbook paľh: projecľ_required_file_v2/ansible.yml in github
repo= https://github.com/Abhishek7884/finalproject
invenľory file paľh: projecľ_required_file_v2/hosľs
And installed the 'docker' python module to run the docker using ansible playbook and
'docker' module should be run for python version>=2.6
the edureka master machine has python version 3.8. So I have installed this 'docker'
module. and modified the ansible inventory file(hosts) in such a way that my ansible should
run using python3.8 version not as a default python2 version. i have modified this inventory
with 'ansible_pyľhon_inľerpreľer="/usr/bin/pyľhon3.8"' parameter along with
hostname otherwise it will use the default python2 version and it will not run using the
'docker' module.
To install this module: pip install docker
If the edureka lab has python version 2.6 i will have to install the 'docker-py' module and
dont need to change the ansible inventory file as ansible use python default version python2.
To install this module: pip install docker-py
and i have installed the ansible module 'community.docker' to build the docker image and run
the container. and this has to be installed in jenkins user separately otherwise it won't
recognize the module and will throw the error so this is very important that i need to install
this module for specific the user that i am running the ansible playbook.
To install this module : ansible-galaxy collection install community.docker
Jenkins and ansible integration process to build the docker image, run the build image
container and then deploy to kubernetes with
deployment,service(nodeport).
Note: I have made sure to copy the deployment.yml and Dockerfile file in the
'/home/edureka/Desktop' folder before doing the below setup.
First i have installed the ansible plugin in manage plugins section of jenkins-> and created
the job 'package_kubernetes_v2' and configured this by giving the git path with main
branch-> and selected the 'Execute shell' in build step for login to the docker with
credentials-> and then choose the 'Invoke Ansible Playbook' and provided the given
playbook path 'project_required_file_v2/ansible.yml', inventory file path
'project_required_file_v2/hosts'. -> and then run the build.
And then created the CI/CD pipeline view as 'CI_CD_KUBERNETEES_V2' and then ran the
pipeline.
command for docker login: sudo docker login -u admin -p <password>
ansible file:
project_required_file_v2/ansible.yml
---
- hosts:
localhost
become: yes
tasks:
- name: Build an image and push it to a private repo
community.docker.docker_image:
build:
path: "/home/edureka/Desktop"
name: docker.io/admin/abctechnologies tag: test
push: true
source: build
register: out
- debug:
var: out
- name: start a container
community.docker.docker_container
:
name: abc-application
image:admin/abctechnologies state:
started
ports:
- 1234:8080
restart:
true register:
out
- debug:
var: out
- name: Deploying to Kubernetes
- name: Create a Deployment by reading the definition from a local file
command: "kubecľl --kubeconfig=/etc/Kubernetes/admin.conf apply -f
/home/edureka/Desktop/deployment.yml"
register: out
- debug:
var: out
---
There are 3 tasks created above in an ansible file.
1) Building the docker image and pushing to docker hub(- name: Build an image and
push it to a private repo )
2) Run the build docker container ( - name: start a container )
3) deploying artifacts to kubernetes with deployment controller and NodePort service
(Create a Deployment by reading the definition from a local file )
- In first task, i am taking a Dockerfile from path '"/home/edureka/Desktop"' to build and
pushing to docker hub repository (docker.io/admin/abctechnologies) and displaying the
output using '-debug module' in ansible.
● The above code will start to build the docker image by taking the Dockerfile from
'/home/edureka/Desktop' directory.
- In second task, i am pulling the docker image (admin/abctechnologies) and running with
custom port exposed to 1234 by providing container port as 8080 and displaying the output
using '-debug' module in ansible.
- In third task, using ansible 'command' module to be used as a shell to run the kubernetes
command to run the deployment.yml file.
And I have given the config path in the ansible file and provided the become:sudo access to
use the admin.conf file to run the deployment.
As part of readiness i have tried to run the ansible-playbook locally not by jenkins and then
tried in jenkins.
Process of deploying the artifacts to kubernetes using ansible i was seen one k8s
kubernetes module available in openshift but i observed in-compatibility issues with the
python. Ansible using python version 2.7.17 internally after installation of ansible but for k8s
module of openshift requires more than 3.6 version even after i followed many solutions
online still ansible could not taking python version as 3.8 or 3.6 and even after i modified
some configurations in the ansible.conf file it’s not loading the k8s module from openshift
unfortunately this all took more than 8 hours for me but still not worked out So i have
followed the approach to run the ansible play-book from jenkins and internally jenkins will
integrate ansible to run the playbook to build the docker image and run the docker container
and then created the deployment and service(NodePort) to deploy our latest version of an
application.
register: out
- debug:
var: out
explanation: Here we need to put the register keyword just below the output you want to
store.
For ex: I have put the 'register' module just below the 'command' module so after
executing this 'command' module line it will store the output (error or success) to ‘out’
variable only, not any other variable.
And in debug we need to make sure to put ‘var’ if we are displaying any output of some
command like above. And ‘msg’ is like echo in linux.
inventory file
project_required_file_v2/hosts
[local]
localhost ansible_python_interpreter="/usr/bin/python3.8"
Dockerfile
/home/edureka/Desktop/Dockerfile
FROM docker.io/library/ubuntu:18.04
RUN apt-get -y update && apt-get -y
upgradeRUN apt-get -y install openjdk-8-jdk
wget RUN mkdir /usr/local/tomcat
ADD
https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.68/bin/apache-tomcat-9.0.68.tar.gz
/tmp/apache-tomcat-9.0.68.tar.gz
RUN cd /tmp && tar xvfz apache-tomcat-9.0.68.tar.gz
RUN cp -Rv /tmp/apache-tomcat-9.0.68/* /usr/local/tomcat/
ADD **/*.war /usr/local/tomcat/webapps
EXPOSE 8080
CMD /usr/local/tomcat/bin/catalina.sh run
explanation: taking an Ubuntu image and modifying the image with installation of java and
tomcat and then deploying the .war file to the tomcat container and running this container.
And Prepared the Deployment and service files for deploying the application.
deployment.yml
/home/edureka/Desktop/deployment.yml
---
kind: Deployment
apiVersion: apps/v1
metadata:
name: abctechnologies-dep
spec:
replicas: 2
minReadySeconds: 45
strategy:
type:
RollingUpdate
rolling Update:
maxUnavailable: 1
maxSurge: 2
selector:
matchLabels:
app: abc-tech-app
template:
metadata
: labels:
app: abc-tech-app
spec:
containers:
- image: admin/abctechnologies name:
app
---
kind: Service
apiVersion: v1
metadata:
name: abc-tech-service
spec:
type:
NodePort
selector:
app: abc-tech-app
ports:
- port: 80 cluster port
targetPort: 8080 container image port
—
explanation:
- acquiring 2 replica pods that match with label 'abc-tech-app' if not found then creating pods
using template using docker image repository (admin/abctechnologies) and exposing the
created pods using service type 'NodePort' for accessing outside of network.
- The deployment file includes service also and has configured the strategy as below in
deployment.The strategy is this deployment needs to follow rolling update strategy which will
upgrade the container with requested version one by one and destroy the older version one
by one.
minReadySeconds: 45 : indicates to wait for 45 seconds time to prepare the new version
pods to initialize (based on maxSurge value)
and this maxUnavailable: 1: indicates that the requested replicas count for the new version
should not be less than 1 while making up the new version pods for application availability.
Pod also created but as i have created deployment already with 2 pod replicas
so i did not used it
---
kind: Pod
apiVersion: v1
metadata:
name: abctechnologies-pod
namespace: default
labels:
role: abc-tech-app
spec:
containers:
- image: admin/abctechnologies:docker_tagname:
app
---
While doing this task i have encounter some issues as below
Issue1:
Permission error
Solution:
And add this permission for jenkins user in /etc/sudoers file,
jenkins ALL=(ALL) NOPASSWD: ALL
Issue2;
Failed to connect to the host via ssh: Warning: Permanently added 'localhost' (ECDSA) to
the list of known hosts.
jenkins@localhost: Permission denied (publickey,password).
Solution:
So added the ssh key(public) to the self jenkins user as well then it works without giving the
above error.
Please find the screenshots of all steps that i have followed:
Downloading the ansible plugin
Plugin download successful screen
Creating the job(package_kubernetes_v2)
Setting up the git repository1
Build step ‘Execute shell’ to login to the docker hub
Choosing ‘Invoke ansible playbook’ option in build step
Giving ansible-playbook path to run from jenkins
Giving ansible inventory file(hosts) to use it to run the playbook
Install the python ‘docker’ module as my python version is >=2.6
After running the build after setting up it got success
Git started getting updated code from github
Docker login and docker push has been started
Deploying to kubernetes has been started
Pacakge_kubernetes_v2 job got success message
Docker image validation in edureka local system
Docker hub push validation
Docker container validation
Docker container validation in browser
Validating kubernetes validation resources(deployment,pods,service)
Validating the kubernetes container with service port
Creating the pipeline(CI_CD_PIPELINE_KUBERNETEES_V2)
Modifying the ‘package_kubernetes_v2) job to watch the test job and trigger
when it completes.
Pipeline started and then compile job has triggered
Pipeline in-progress
Pipeline has completed successfully with all three jobs
Validating package_kubernetes_v2) job status stating who trigger(started by
upstream project ‘test’)
Package_kubernetes_v2 job success log
Docker resources validation:
Docker hub validation
Docker container port validation in browser
Kubernetes resources validation
Kubernetes service port validation in browser
References i have followed:
https://docs.ansible.com/ansible/latest/collections/community/docker/docker_image_module.
html
https://docs.ansible.com/ansible/latest/collections/community/docker/docker_container_mod
ule.html
https://github.com/ansible-collections/community.docker
https://pypi.org/project/docker/
https://pypi.org/project/docker-py/
https://github.com/ansible-collections/community.docker
https://docker-py.readthedocs.io/en/latest/
https://www.baeldung.com/ops/docker-removing-images#:~:text=Forcefully%20Remove%20
Containers%20and%20Images&text=The%20%2Df%20flag%20is%20used,the%20running
%20Docker%20containers%20forcefully.&text=The%20docker%20images%20%2Dqa%20wi
ll,forcefully%20remove%20the%20Docker%20image
https://stackoverflow.com/questions/22769568/system-specific-variables-in-ansible
https://stackoverflow.com/questions/60834692/how-to-completely-remove-ansible-2-8-3-on-u
buntu-18-04
--
https://docs.ansible.com/ansible/2.6/modules/k8s_module.html#examples
https://docs.ansible.com/ansible/latest/user_guide/guide_rolling_upgrade.html
https://adamtheautomator.com/ansible-kubernetes/
https://adamtheautomator.com/ansible-template/
ansible-playbook sample-playbook.yml -e 'ansible_python_interpreter=/usr/bin/python3' -
https://docs.ansible.com/ansible/latest/reference_appendices/python_3_support.html
https://docs.ansible.com/ansible/2.9/modules/k8s_service_module.html
https://github.com/DeekshithSN/sample-web-application -
https://www.youtube.com/watch?v=NSk0NHkTjDs
https://www.baeldung.com/ops/jenkins-parameterized-builds
https://stackoverflow.com/questions/56003777/how-to-pass-environment-variable-in-kubectldeployment
https://stackoverflow.com/questions/62108860/kubectl-no-matches-for-kind-service-in-versio
n-apps-v1
https://stackoverflow.com/questions/59579482/kubectl-apply-error-from-server-forbidden-aut
hentication-required-jenkins
https://stackoverflow.com/questions/51489359/docker-using-password-via-the-cli-is-insecure
-use-password-stdin
https://kubernetes.io/docs/reference/kubectl/cheatsheet/
Task 5: Using Prometheus, monitor the resources like CPU utilization: Total Usage, Usage
per core, usage breakdown, memory, and network on the instance by providing the
endpoints on the local host. Install the node exporter and add the URL to the target in
Prometheus. Using this data, log in to Grafana and create a dashboard to show the metrics.
Approach i have followed:
First of all we need to have prometheus,Grafana but edureka lab already installed these
tools. So I had installed the node-exporter in master node to monitor the metrics of a node
and added the target url in the prometheus.yml file so that prometheus will start to monitor.
And I have monitored and captured the CPU,memory and network of the target node. And I
have created a dashboard by selecting the prometheus app from Grafana and then created
a Panel for visualizing the metrics in Grafana.
After installing node_exporter I have added the below job in the prometheus.yml file to get
the metrics from the target.
—---------
- job_name: 'node_exporter'
scrape_interval: 5s
static_configs:
- targets: ['localhosľ:9100']
—---------
/opt/prometheus-2.27/prometheus.yml
my global config
global:
scrape_interval: 15s Set the scrape interval to every 15 seconds. Default
is every 1 minute.
evaluation_interval: 15s Evaluate rules every 15 seconds. The default is every 1
minute.
scrape_timeout is set to the global default (10s).
Alertmanager configuration
alerting:
alertmanagers:
- static_configs:
- targets:
- alertmanager:9093
Load rules once and periodically evaluate them according to the
global'evaluation_interval'.
rule_files:
- "first_rules.yml"
- "second_rules.yml"
A scrape configuration containing exactly one endpoint to scrape:
Here it’s Prometheus itself.
scrape_configs:
The job name is added as a label `job=<job_name>` ľo any timeseries scraped
from this config.
- job_name: 'Prometheus'
metrics_path defaults to '/metrics'
scheme defaults to 'help'.
static_configs:
- targets: ['localhosľ:9090']
- job_name: 'node_exporter'
scrape_interval: 5s
sľaľic_configs:
- targets: ['localhosľ:9100']
Please find the screenshots:
Prometheus self monitoring
Graph visualization for the metrics in prometheus
Prometheus application self target before adding our required target
Alerts tab: If we configured alertmanager it will list the alerts here
node exporter data validation through target
added_target in prometheus file
Prometheus_targets page with node exporter of a node
cpu usage breakdown for node
total count of cpu usage in seconds from starting
Total count of cpu in seconds from starting
Rate of growth for cpu in last 5 minutes
Rate of growth for cpu in 5 minutes graph
CPU Utilization
CPU Utilization graph
Some of the commands i have used for CPU monitoring
Memory monitoring
Node memory available in bytes:
Node memory available in MB
Node memory available in MB for last 5min
memory usage in percentage
Memory Available by Node
Network monitoring
Load average in percentage:
Load Average per Instance:
Network inbound traffic per Node:
Network outbound traffic per Node
Grafana screenshots:
Grafana home page:
Grafana data source selection(prometheus):
Setting up the prometheus target:
Adding panel for prometheus:
Cpu monitoring 1
Cpu monitoring 2
Cpu monitoring 3
Memory monitoring 1
Memory monitoring 2
Memory monitoring 3
Network load monitoring 1
Network load monitoring 2
Network monitoring 3
Network load monitoring 4
Using different visualization graphs(Gauge)-cpu breakdown
Using different visualization graphs 2
Commands i have used for prometheus:
Thank you
