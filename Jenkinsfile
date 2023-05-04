pipeline {
    agent {
        label('master')
    }
    
    options {
        githubProjectProperty(displayName: 'java.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
        githubProjectProperty(displayName: 'node.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

   stages {
        stage('Read properties and checkout') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git']])
                    def props = readProperties file: 'java.properties'
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
                        library("${props['javaLibrary']}")
                        javaGrVars.test()
                        javaGrVars.PullDjava("${env.JAVAIMAGE}")
                        javaGrVars.buildDjava("${env.JAVAIMAGE}")
                        
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

