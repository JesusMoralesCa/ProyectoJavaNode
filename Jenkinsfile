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
                    def file = readProperties file: 'project.properties'

                    if (file['tecnology'] == 'java') {
                                
                                    
                                        script {
                                            withEnv(["Java=11"]) {
                                                library("java-lib")
                                                javaGrVars.test()
                                                javaGrVars.setProperties()
                                                javaGrVars.build()
                                            }
                                        }
                                    
                                

                    } else if (file['tecnology'] == 'node') {
                         
                            
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
            }
        }
    }
}
