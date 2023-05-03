pipeline {
    agent any
    
    environment {
        java = properties('java.version=11')
        node = properties('nodejs.version=14.18.0')
    }

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages {
        stage('Java stage') {
            environment {
                java
                //JAVA_11 = properties('java.version=11')
                CLASSPATH = library('java-lib')
                
            }
            steps {
                script {
                    javaGrVars.test()
                }
            }
        }
        stage('Node.js stage') {
            environment {
                node
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
