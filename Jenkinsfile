

pipeline{
    agent any

    options{
    githubProjectProperty(displayName: 'project.properties', projectUrlStr: 'https://github.com/JesusMoralesCa/ProyectoJavaNode.git')
}
    
  stages {
      
       environment {
        JAVA_11 = properties('java.version=11')
        NODE_14 = properties('nodejs.version=14.18.0')
    }
      
      
      
      /*
      stage('Build'){
         environment {
                // Establece la versión de Java a partir de las propiedades del archivo
                JAVA_11 = properties('java.version=11')
                // Establece la versión de Node.js a partir de las propiedades del archivo
                NODE_14 = properties('nodejs.version=14.18.0')
            }
      }
      */
      stage('Java stage') {
            environment {
                CLASSPATH = library('java-lib')
            }
            steps {
                 javaGrVars.test()
            }
        }
        stage('Node.js stage') {
            environment {
                PATH = library('node-lib')
            }
            steps {
                nodeGrVars.test()
            }
        }
     }
}
