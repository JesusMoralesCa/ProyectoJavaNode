pipeline {
    agent any

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

   stages {
        stage('Read properties and checkout') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git']])
                    def props = readProperties file: 'project.properties'
                    env.JAVA_LIBRARY = props['javaLibrary']
                }
            }
        }

        stage('Java stage') {
            steps {
                script {
                    withEnv(["java=${env.JAVA_VERSION}"]) {
                        library("${env.JAVA_LIBRARY}")
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

