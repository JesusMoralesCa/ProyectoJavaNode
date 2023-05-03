pipeline {
    agent any
    

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages {
        stage('Java stage') {
           
            steps {
                script {
                    load 'project.properties'
                    javaGrVars.test()
                }
            }
        }
        stage('Node.js stage') {
            
            steps {
                script {
                    load 'project.properties'
                    nodeGrVars.test()
                }
            }
        }
    }
}
