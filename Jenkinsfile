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
                    env.JAVAIMAGE = props['imageJava']
                    env.NODE_LIBRARY = props['nodeLibrary']
                    
                }
            }
        }

        stage('Java stage') {
            steps {
                script {
                    withEnv(["java=${env.JAVA_VERSION}"]) {
                        library("${env.JAVA_LIBRARY}")
                        javaGrVars.test()
                        //javaGrVars.buidDjava()
                        
                    }
                }
            }
        }

        stage('Node.js stage') {
            steps {
                script {
                    withEnv(["node=${env.NODE_VERSION}"]) {
                        library("${env.NODE_LIBRARY}")
                        nodeGrVars.test()
                    }
 
                }
            }
        }
    }
}

