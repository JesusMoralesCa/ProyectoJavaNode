pipeline {
    agent {
        label('master')
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
                    withEnv(["PATH+NODE=${tool 'Node'}"]) {
                            DOCKERHUB_CREDENTIALS = credentials('docker-hub-jesusmoralesc')
                            library("node-lib")
                            nodeGrVars.build()
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

}
