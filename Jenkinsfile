pipeline {
    agent any
    

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages {
        
        stage('Download .properties file') {
            steps {
                script {
                    
                    sh 'curl -L -o project.properties https://github.com/JesusMoralesCa/ProyectoJavaNode/main/project.properties'
                }
            }
        }
        
        
        
        
        
        stage('Java stage') {
          
            steps {
                script {
                    
                    def props = readProperties file: 'project.properties'
                    def javaLib = props['java.library']
                    def javaVersion = props['java.version']
                    
            environment {
                CLASSPATH = library(javaLib)
                JAVA_HOME = tool(javaVersion)
            }
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
