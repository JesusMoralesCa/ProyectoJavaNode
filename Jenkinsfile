pipeline {
    agent any

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages {
        stage('Java stage') {
            environment {
                //CLASSPATH = library('java-lib')
                JAVA_CLASSPATH
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
