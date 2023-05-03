


pipeline {
    agent any
    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages{
        
        
        stage('Java stage') {
            environment {
                CLASSPATH = "${project['java.library']}"
            }
            steps {
                echo "${project['java.version']}"
                javaGrVars.test()
            }
        }
        stage('Node.js stage') {
            environment {
                CLASSPATH = "${project['node.library']}"
            }
            steps {
                nodeGrVars.test()
            }
        }
    }
}
