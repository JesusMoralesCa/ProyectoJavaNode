


pipeline {
    agent any
    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

    stages{
        
        
        stage('Java stage') {
            environment {
                //CLASSPATH = "${project['java.library']}"
                CLASSPATH = library('java-lib')
            }
            steps {
                echo "${project['java.version']}"
                javaGrVars.test()
            }
        }
        stage('Node.js stage') {
            environment {
                //CLASSPATH = "${project['node.library']}"
                CLASSPATH = library('node-lib')

            }
            steps {
                nodeGrVars.test()
            }
        }
    }
}
