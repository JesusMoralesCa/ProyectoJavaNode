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

        stage('Java stage') {
            steps {
                script {
                    withEnv(["Java=11"]) {
                        library("java-lib")
                        javaGrVars.test()
                        javaGrVars.setProperties()
                        javaGrVars.build()
                        
                        
                    }
                }
            }
        }

        stage('Node.js stage') {
            steps {
                script {
                    withEnv(["Node=14"]) {
                        library("node-lib")
                        nodeGrVars.test()
                        nodeGrVars.setProperties()
                        nodeGrVars.build()
                    }
 
                }
            }
        }
    }
}

