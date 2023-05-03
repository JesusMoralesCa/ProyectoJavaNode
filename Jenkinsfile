pipeline {
    agent any

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages {
        stage('Java stage') {
            environment {
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
