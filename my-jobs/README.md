#Jenkins job files

## Run Jenkins
- Create a local folder to save workspace data
``````bash
mkdir -p jenkins-data
``````

### Docker image
Docker image with Java 1.7+, Apache Maven 3.9.x, Python 3.9.x, JFrog CLI 2.57.x
- Prerequisite: Docker v 25x. 
``````bash
docker run -d -p 7080:8080 --volume $(pwd)/jenkins-data:/var/jenkins_home -rm --name jenkins/jenkins:latest &
``````

### WAR file
- Prerequisite: Java 1.7+.     
``````bash
wget https://get.jenkins.io/war/latest/jenkins.war
java -jar jenkins.war --httpPort=7080 --enable-future-java & 
``````

- Initial setup password
``````bash
cat $(pwd)/jenkins-data/secrets/initialAdminPassword
``````
- Turn off user access
``````bash
cat $(pwd)/jenkins-data/config.xml | grep useSecurity
``````
- output should be <useSecurity>false</useSecurity> else update true to false.
- restart jenkins http://localhost:7080/exit
    - refer https://wiki.jenkins-ci.org/display/JENKINS/Administering+Jenkins


## Jenkins secrets
### JFrog CLI Bearer token
![JFrog CLI](./images/JF_CLI_BearerToken.png)



[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fkrishnamanchikalapudi&count_bg=%2379C83D&title_bg=%23555555&icon=github.svg&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://github.com/krishnamanchikalapudi)
