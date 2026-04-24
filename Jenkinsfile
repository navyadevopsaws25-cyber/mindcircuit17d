pipeline {
    agent any stages {
        trigger{
            gitpush()
        }
     stage('Git Clone') {
            steps {
                echo 'clonig from github repo'
            git branch: 'main', url: 'https://github.com/navyadevopsaws25-cyber/mindcircuit17d.git'         
        }
        }

         stage('build artifact') {
            steps {
                echo 'building artifact using maven'
                sh 'mvn clean install'
            }
        }
    stage('build artifact') {
            steps {
                echo 'building artifact using maven and deployoing on nexus'
                sh 'mvn clean deploy'
            }
        }

        stage('Deploy to tomcat') {
            steps {
                echo 'deploying on tomcat web'
          deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://34.224.82.8:8081//')], contextPath: 'navya', war: '**/*.war'        
            }
        }

    }}


