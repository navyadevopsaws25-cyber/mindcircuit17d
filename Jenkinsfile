pipeline {
    agent any
    stages {


        stage('Git Clone') {
            steps {
                echo 'clonig from github repo'
             git branch: 'main', url: 'https://github.com/navyadevopsaws25-cyber/mindcircuit16d.git'
            }
        }

         stage('build artifact') {
            steps {
                echo 'building artifact using maven'
                sh 'mvn clean install'
            }
        }
   

        stage('Deploy to tomcat') {
            steps {
                echo 'deploying on tomcat web'
          deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://ec2-54-242-132-214.compute-1.amazonaws.com:8090/')], contextPath: 'MC-APP', war: '**/*.war'
            }
        }

    }
}
