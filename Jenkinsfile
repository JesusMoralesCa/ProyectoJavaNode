pipeline {
    agent any
    

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    
    environment {
        JAVA_VERSION = "11"
        library 'java-lib'
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
          
          
            
            steps {
                script {
                     withEnv(["java=${java}"]) {
                      
                        javaGrVars.test()
                    }
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
