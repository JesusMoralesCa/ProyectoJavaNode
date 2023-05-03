def libraryVersion
if (env.JAVA == 'JAVA') {
    libraryVersion = project.getProperty('JAVA.java-lib')
} else if (env.NODE == 'NODE') {
    libraryVersion = project.getProperty('NODE.node-lib')
} 


pipeline {
    agent any
    

    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages {
        stage('Java stage') {
            environment {
                JAVA = properties('JAVA')
            }
            steps {
                script {
                    
                    javaGrVars.test()
                }
            }
        }
        stage('Node.js stage') {
              environment {
                NODE = properties('NODE')
            }
            
            steps {
                script {
                    
                    nodeGrVars.test()
                }
            }
        }
    }
}
