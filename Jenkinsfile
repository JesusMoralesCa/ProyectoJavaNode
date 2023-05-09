pipeline {
    agent {
        label('master')
    }
    
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-jesusmoralesc')
        
    }
    
   stages {
        stage('Read properties and checkout') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git']])
                    def file = readProperties file: 'project.properties'
                    env.image = file['imageName']
                    
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
