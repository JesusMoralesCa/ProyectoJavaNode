


pipeline {
    agent any
    options {
        githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
    }

        
        
        stage('Java stage') {
            environment {
                CLASSPATH = "${['java.library']}"
            }
            steps {
                javaGrVars.test()
            }
        }
        stage('Node.js stage') {
            environment {
                CLASSPATH = "${['node.library']}"
            }
            steps {
                nodeGrVars.test()
            }
        }
    }
}
