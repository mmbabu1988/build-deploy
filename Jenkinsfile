pipeline {
    agent any
    triggers {
  cron 'H/5 * * * *'
}

    tools{
        maven 'Apache Maven 3.6.3'
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
            deploy adapters: [tomcat8(credentialsId: 'tomcat-cred', path: '', url: 'http://13.127.206.168:9090/')], contextPath: null, war: '**/*.war'
                 }
    }
}
}
