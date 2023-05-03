def props;


pipeline {
    agent any
    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }
    stages {
        
        stage('Read properties file'){
            props = readProperties file: 'project.properties'
        }
        
        
        stage('Java stage') {
            environment {
                CLASSPATH = "${props['java.library']}"
            }
            steps {
                javaGrVars.test()
            }
        }
        stage('Node.js stage') {
            environment {
                CLASSPATH = "${props['node.library']}"
            }
            steps {
                nodeGrVars.test()
            }
        }
    }
}
