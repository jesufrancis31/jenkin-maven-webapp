#!groovy
node ('node1') {
    label 'node1-label'
    properties([
    buildDiscarder(logRotator(numToKeepStr: '3')),
        properties([enableConcurrentBuilds()])
])
    def mavenHome= tool name: 'mave3.6.1', type: 'maven'
    stage ('checkout GIT code') {
        git credentialsId: 'dca1cbd9-d1da-4d0d-a3c7-6ef298949bed', url: 'https://github.com/jesufrancis31/jenkin-maven-webapp.git'
    }
    stage ('build MAVEN code') {
        sh "${mavenHome}/bin/mvn clean package"
    }
   /*stage ('Execute SONARQUBE Reports') {
        sh "${mavenHome}/bin/mvn sonar:sonar"
    }
    stage ('Upload Artifacts to Nexus'){
        sh "${mavenHome}/bin/mvn deploy"
    }
    stage ('Deploy app in to wildfly') {
    sh "scp ${WORKSPACE}/target/*.war root@18.219.72.28:/home/ec2-user/wildfly/wildfly-16.0.0.Final/standalone/deployments"
} */
    
}
   stage ('emailNotification')
   {
       emailext attachLog: true, body: 'The Maven Web Application Project Build is Successful...!', subject: 'Build Success', to: 'jesu.devops@gmail.com'
   }

stage ('SendEmailNotification') {
emailext body: 'Build is Over', subject: 'Build is Over', to: 'jesu.devops@gmail.com' 

}
