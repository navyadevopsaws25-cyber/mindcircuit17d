pipeline {
    agent any
    tools{
        maven 'Maven_3.9.11'
    }
    
       stages {
     stage('Git Clone') {
            steps {
                echo 'clonig from github repo'
            git branch: 'main', url: 'https://github.com/navyadevopsaws25-cyber/mindcircuit17d.git'         
        }
        }

        stage('sonarqube scan') {
            steps {
                echo 'This stage scans the code using sonarqube'
                sh 'ls -ltrh'
                
                sh ''' mvn sonar:sonar \\
                      -Dsonar.host.url=http://13.217.107.205:9000 \\
                      -Dsonar.login=squ_6f842bd4dc776de375a9b6257db22632edd77c69'''
            }
    	}		
		
        stage('Build Artifact') {
            steps {
                echo 'This stage builds the code using maven'
				sh 'mvn clean install'			
				
            }
        }
      stage('Deploy to Tomcat') {
            steps {
                echo 'This stage deploys .war to tomcat webserver'
               deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://13.217.107.205:8081/')], contextPath: 'app', war: '**/*.war'
            }
        }		
       

    }}
