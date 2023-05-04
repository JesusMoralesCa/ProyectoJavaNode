pipeline {
    agent {
        label('master')
    }
    
   stages {
        stage('Read properties and checkout') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git']])
                    def props = readProperties file: 'java.properties'
                    def props2 = readProperties file: 'node.properties'
                    env.JAVA_LIBRARY = props['javaLibrary']
                    env.JAVAIMAGE = props['imageJava']
                    env.NODE_LIBRARY = props2['nodeLibrary']
                    
                }
            }
        }

        stage('Java stage') {
            steps {
                script {
                    withEnv(["java=${env.JAVA_VERSION}"]) {
                        library("java-lib")
                        javaGrVars.test()
                        javaGrVars.PullDjava("${env.JAVAIMAGE}")
                        
                        
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

