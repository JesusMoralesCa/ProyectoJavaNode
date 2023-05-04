pipeline {
    agent {
        label('master')
    }
    
   stages {
        stage('Read properties and checkout') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git']])
                    
                    
                }
            }
        }

stage('Leer archivo') {
            steps {
                script {
                    def file = findFiles glob: "**/*.js"
                    if (file.endsWith('.java')) {
                                stage('Java stage') {
                                    steps {
                                        script {
                                            withEnv(["Java=11"]) {
                                                library("java-lib")
                                                javaGrVars.test()
                                                javaGrVars.setProperties()
                                                javaGrVars.build()
                                            }
                                        }
                                    }
                                }

                    } else if (file.endsWith('.js')) {
                         stage('Node.js stage') {
                            steps {
                                script {
                                    withEnv(["Node=14"]) {
                                        library("node-lib")
                                        nodeGrVars.test()
                                        nodeGrVars.setProperties()
                                        nodeGrVars.build()
                                    }
                                }
                            }
                        }
                    } else {
                        error "Archivo con extensión desconocida: ${file}"
                    }
                }
            }
        }

    }
}
