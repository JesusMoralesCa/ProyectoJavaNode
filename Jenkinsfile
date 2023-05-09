pipeline {
    agent {
        label('master')
    }
    
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-jesusmoralesc')
        file = readProperties file: 'project.properties'
        image = file['imageName']
    }
    
   stages {
        stage('Read properties and checkout') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git']])
                    
                    
                }
            }
        }





stage('Build') {
            steps {
                script {
                    withEnv(["PATH+NODE=${tool 'maven'}"]) {
                            library("java-node")
                            W2Build()
                            
                   }
                }
            }
        }
    }
    
    post {
        always {
            sh 'docker logout'
        }
    }
}
