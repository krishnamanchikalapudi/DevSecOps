node {
    projectName = "examples.java";
    gitUrl = "https://github.com/krishnamanchikalapudi/${projectName}"
    mailRecipients = "krishna dot manchikalapudi at gmail dot com"
    buildVersion="1.0.0.${BUILD_NUMBER}"
    containerName="${projectName}:${buildVersion}"
    envConfigName="${projectName}-${buildVersion}.zip"

    stageCheck="";
    environment { 
        softwareVersion()
    }
    try {
        stage ("Source Code") {
            stage ("> tag") {
                try {
                    timeout(time: 5, unit: 'MINUTES') {
                        // TODO: 

                        stageCheck += "<br/> Source Code > tag: <font color='green'><b>OK</b></font>"
                    }
                } catch (ex) {
                    stageCheck += "<br/> Source Code > tag: <font color='red'><b>ERROR</b></font>"
                }
            }
            stage ("> checkout") {
                try {
                    timeout(time: 5, unit: 'MINUTES') {
                        // TODO: refer example: GitCheckout/Jenkinsfile
                
                        stageCheck += "<br/> Source Code > checkout: <font color='green'><b>OK</b></font>"
                    }
                } catch (ex) {
                    stageCheck += "<br/> Source Code > checkout: <font color='red'><b>ERROR</b></font>"
                }
            } 
            stage ("> compile") {
                try {
                    timeout(time: 5, unit: 'MINUTES') {
                        // TODO: 
                    
                        stageCheck += "<br/> Source Code > compile: <font color='green'><b>OK</b></font>"
                    }
                } catch (ex) {
                    stageCheck += "<br/> Source Code > compile: <font color='red'><b>ERROR</b></font>"
                }
            }
            stage ("> unitTests") {
                try {
                    timeout(time: 5, unit: 'MINUTES') {
                        // TODO:

                        stageCheck += "<br/> Source Code > unitTests: <font color='green'><b>OK</b></font>"
                    }
                } catch (ex) {
                    stageCheck += "<br/> Source Code > unitTests: <font color='red'><b>ERROR</b></font>"
                }
            }
        }
        stage ("Secure Coding") {
            parallel staticAnalyser: {
                stage ("> staticAnalyser") {
                    try {
                        timeout(time: 15, unit: 'MINUTES') {
                            // TODO: SonarQube, Fortify, Coverity, Veracode, FindBugs

                            stageCheck += "<br/> Secure Coding > staticAnalyser: <font color='green'><b>OK</b></font>"
                        }
                    } catch (ex) {
                        stageCheck += "<br/> Secure Coding > staticAnalyser: <font color='red'><b>ERROR</b></font>"
                    }
                }
            }, dependencyCompliance: {
                stage ("> dependencyCompliance") {
                    try {
                        timeout(time: 15, unit: 'MINUTES') {
                            // TODO: BlackDuck, SonaType

                            stageCheck += "<br/> Secure Coding > dependencyCompliance: <font color='green'><b>OK</b></font>"
                        }
                    } catch (ex) {
                        stageCheck += "<br/> Secure Coding > dependencyCompliance: <font color='red'><b>ERROR</b></font>"
                    }
                }
            }
        }
        stage ("Package") {
            parallel createContaier: {
                stage ("> container") {
                    try {
                        timeout(time: 5, unit: 'MINUTES') {
                            // TODO: generate container
                            echo "containerName: ${containerName}"
                           
                            stageCheck += "<br/> Package > contaier: <font color='green'><b>OK</b></font>"
                        }
                    } catch (ex) {
                        stageCheck += "<br/> Package > contaier: <font color='red'><b>ERROR</b></font>"
                    }
                }
            }, environmentConfig: {
                stage ("> envConfig") {
                    try {
                        timeout(time: 5, unit: 'MINUTES') {
                            // TODO: zip deploy/k8s folder
                           
                            echo "envConfigName: ${envConfigName}"
                            stageCheck += "<br/> Package > envConfig: <font color='green'><b>OK</b></font>"
                        }
                    } catch (ex) {
                        stageCheck += "<br/> Package > envConfig: <font color='red'><b>ERROR</b></font>"
                    }
                }
            }
        }
        stage ("Repository") {
            parallel containerUpload: {
                stage ("> container") {
                    try {
                        timeout(time: 5, unit: 'MINUTES') {
                            // TODO: generate container
                            echo "containerName: ${containerName}"
                           
                            stageCheck += "<br/> Package > container: <font color='green'><b>OK</b></font>"
                        }
                    } catch (ex) {
                        stageCheck += "<br/> Package > container: <font color='red'><b>ERROR</b></font>"
                    }
                }
            }, environmentConfig: {
                stage ("> envConfig") {
                    try {
                        timeout(time: 5, unit: 'MINUTES') {
                            // TODO: zip deploy/k8s folder
                            echo "envConfigName: ${envConfigName}"

                            stageCheck += "<br/> Package > envConfig: <font color='green'><b>OK</b></font>"
                        }
                    } catch (ex) {
                        stageCheck += "<br/> Package > envConfig: <font color='red'><b>ERROR</b></font>"
                    }
                }
            }
        }
        stage ("ENV:DEV Deploy ") {
            parallel deployContaier: {
                stage ("> container") {
                    try {
                        timeout(time: 5, unit: 'MINUTES') {
                            // TODO: generate container
                            echo "containerName: ${containerName}"

                            stageCheck += "<br/> ENV:DEV Deploy > container: <font color='green'><b>OK</b></font>"
                        }
                    } catch (ex) {
                        stageCheck += "<br/> ENV:DEV Deploy > container: <font color='red'><b>ERROR</b></font>"
                    }
                }
            }, environmentConfig: {
                stage ("> envConfig") {
                    try {
                        timeout(time: 5, unit: 'MINUTES') {
                            // TODO: zip deploy/k8s folder
                            echo "envConfigName: ${envConfigName}"

                            stageCheck += "<br/> ENV:DEV Deploy > envConfig: <font color='green'><b>OK</b></font>"
                        }
                    } catch (ex) {
                        stageCheck += "<br/> ENV:DEV Deploy > envConfig: <font color='red'><b>ERROR</b></font>"
                    }
                }
            }
        }
        stage ("ENV:DEV Function Tests") {
            try {
                timeout(time: 5, unit: 'MINUTES') {
                    // TODO: refer example: Approval/Jenkinsfile

                    stageCheck += "<br/> ENV:DEV Function Tests: <font color='green'><b>OK</b></font>"
                }
            } catch (ex) {
                stageCheck += "<br/> ENV:DEV Function Tests: <font color='red'><b>ERROR</b></font>"
            }
        }
        stage ("Promote 2 ENV:QA?") {
            try {
                timeout(time: 1, unit: 'MINUTES') {
                    // TODO: refer example: Approval/Jenkinsfile
                    sleep 65
                    stageCheck += "<br/> Promote 2 ENV:QA? : <font color='green'><b>OK</b></font>"
                }
            } catch (org.jenkinsci.plugins.workflow.steps.FlowInterruptedException e) {
                echo "Promote 2 ENV:QA? Aborted by " + e.causes.get(0).getUser().toString()
                stageCheck += "<br/> Promote 2 ENV:QA? : <font color='red'><b>ERROR</b></font>"
            } catch (ex) {
                stageCheck += "<br/> Promote 2 ENV:QA? : <font color='red'><b>ERROR</b></font>"
            }
        }
    } catch (err) {
        echo 'I failed :('
    } finally {
        emailBody = "Console log: ${BUILD_URL}console <BR/> Build Status: ${currentBuild.currentResult} <BR/><BR/> Job Summary:  ${stageCheck} "
        if (currentBuild.result == 'UNSTABLE') {
            echo 'I am unstable :/'
        } else {
            echo 'I succeeeded!'

            emailext body: "${emailBody}",
            mimeType: 'text/html',
            subject: "[Jenkins] ${JOB_NAME}: ${BUILD_NUMBER} - ${currentBuild.currentResult}",
            to: "${mailRecipients}",
            replyTo: "${mailRecipients}",
            recipientProviders: [[$class: 'CulpritsRecipientProvider']]
        }
    }
    print "$emailBody"
}

def softwareVersion() {
    sh """ #!/bin/bash
            echo '\n ***** Languages'
        java -version
        npm -version
            echo '\n ***** Java build tools'
        mvn -version
        gradle -version
            echo '\n ***** Container Orchestration'
        docker version
        kubectl version
        echo '\n'
    """
}
def deployContainer(envHost) {

}
def deployEnvironmentConfig(envHost) {

}