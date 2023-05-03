pipeline {
    agent any
    

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages {
        
        stage('checkout') {
          checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git']])
        }
        stage('Read properties'){
            props = readProperties file: 'project.properties'
        }
        
        
        
        
        stage('Java stage') {
          
            environment {
                CLASSPATH = "${project['java.library']}"
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
