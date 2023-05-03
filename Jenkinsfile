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
                    echo "HOLA ${props['envJava']}"
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
                     withEnv(["java=${envJava}"]) {
                        //library 'java-lib'
                         library "${props['javaLibrary']}"
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
