pipeline {
    agent any
    triggers {
  cron 'H/10 * * * *'
}

    tools{
        maven 'Apache Maven 3.8.7'
    }
    options {
  buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '2')
}


    stages {
        stage('Clone the repository') {
            steps {
               git credentialsId: 'Github_username_password', url: 'https://github.com/mmbabu1988/build-deploy.git'
            }
        }


        stage('Build the maven code') {
            steps {
            sh 'mvn clean install'
                 }
    }

stage('Deploy to tomcat') {
            steps {
            deploy adapters: [tomcat8(credentialsId: 'Tomcat_username_password', path: '', url: 'http://54.224.167.178:9090/')], contextPath: null, war: '**/*.war'
                 }
    }
}
}
