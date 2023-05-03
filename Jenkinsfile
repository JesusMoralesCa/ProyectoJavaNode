pipeline {
    agent any

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    environment {
        JAVA_VERSION = "11"
        JAVA_LIBRARY = ""
    }

    stages {
        stage('Read properties') {
            steps {
                script {
                    def props = readProperties file: 'project.properties'
                    env.JAVA_LIBRARY = props['javaLibrary']
                    echo "HOLA ${props['javaLibrary']}"
                }
            }
        }

        stage('checkout') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git']])
                }
            }
        }

        stage('Java stage') {
            steps {
                script {
                    withEnv(["java=${JAVA_VERSION}"]) {
                        library("${JAVA_LIBRARY}")
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
