#Jenkins job files

## Run Jenkins
- Create a local folder to save workspace data
``````bash
mkdir -p my-jenkins-data
``````
### Docker image
Docker image with Java 1.7+, [Apache Maven 3.9.x](https://maven.apache.org), [Python 3.9.x](https://www.python.org/downloads/), [JFrog CLI 2.57.x](https://jfrog.com/getcli/)
- Prerequisite: Docker v 25x. 
``````bash
docker run -d -p 7080:8080 --volume $(pwd)/my-jenkins-data:/var/jenkins_home -rm --name jenkins/jenkins:latest &
``````
### WAR file
- Prerequisite: Java 1.7+, [JFrog CLI](https://jfrog.com/getcli/), [Apache Maven](https://maven.apache.org)
``````bash
wget https://get.jenkins.io/war/latest/jenkins.war
java -jar jenkins.war --httpPort=7080 --enable-future-java & 
``````

- Initial setup password
``````bash
cat $(pwd)/my-jenkins-data/secrets/initialAdminPassword
``````
- Turn off user access
``````bash
cat $(pwd)/my-jenkins-data/config.xml | grep useSecurity
``````
- output should be <useSecurity>false</useSecurity> else update true to false.
- restart jenkins http://localhost:7080/exit
    - refer https://wiki.jenkins-ci.org/display/JENKINS/Administering+Jenkins


## Jenkins jobs
- secret credentials
![JFrog CLI](./images/JenkinsSecrets.png)
- [software](./software.jenkinsfile)
![software.jenkinsfile](./images/sofware_jenkinsfile.png)
- [spring-petclinic using JFrog CLI](./spring-petclinic-JFcli.jenkinsfile)
![spring-petclinic-JFcli.jenkinsfile](./images/spring-petclinic-JFcli_jenkinsfile.png)



## GitHub 
### Last uncommit
- 1 is last uncommit
``````bash
git reset --hard HEAD~1
git push origin -f
``````
- 4 is last uncommit
``````bash
git reset --hard HEAD~4
git push origin -f
``````

### Remove last add cache
``````bash
git rm -r --cached .
``````

[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fkrishnamanchikalapudi&count_bg=%2379C83D&title_bg=%23555555&icon=github.svg&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://github.com/krishnamanchikalapudi)
