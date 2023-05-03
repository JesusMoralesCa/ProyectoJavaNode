pipeline {
    agent any
    

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages {
        
    stage('Read properties'){
            steps {
                script {
                    def props = readProperties file: 'project.properties'
                    env.Java = props['java.library']
                }
            }
        }

        stage('checkout') {
            steps {
                script{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git']])
                }
            }
         }
        
        
        
        
        
        stage('Java stage') {
          
            environment {
                
                CLASSPATH = library(env.Java)
                //CLASSPATH  = library('node-lib')
            }
            
            steps {
                script {
                    
                    javaGrVars.test()
                }
            }
        }
        stage('Node.js stage') {
            environment {
                
                CLASSPATH  = library('node-lib')
            }
            steps {
                script {
                    nodeGrVars.test()
                }
            }
        }
    }
}
