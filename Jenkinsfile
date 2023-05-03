pipeline {
    agent any
    

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages {
        
        stage('Download .properties file') {
            steps {
                script {
                    sh 'curl -L -o project.properties https://raw.githubusercontent.com/JesusMoralesCa/ProyectoJavaNode/main/project.properties'
                }
            }
        }
        
        
        
        
        
        stage('Java stage') {
            environment {
                
                //JAVA_11 = properties('java.version=11')
                //CLASSPATH = library('java-lib')
                CLASSPATH = "${project['java.library']}"
                
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
