properties([
    pipelineTriggers([pollSCM('')]), 
    [$class: 'FilePathJobProperty', 
        filePath: 'project.properties']
])


pipeline{
    agent any
  options {
      // Define las bibliotecas compartidas para el entorno de Node.js
        library('node-lib') allowUndefinedParameters: true
        environment name: 'NODE_14', value: '14.18.0'
        // Define las bibliotecas compartidas para el entorno de Java
        library('java-lib') allowUndefinedParameters: true
        environment name: 'JAVA_11', value: '11'
    }
  

  stages {
    stage('Test') {
            environment {
                // Establece la versión de Java a partir de las propiedades del archivo
                JAVA_11 = properties('java.version=11')
                // Establece la versión de Node.js a partir de las propiedades del archivo
                NODE_14 = properties('nodejs.version=14.18.0')
            }
        
          steps{
                script{
                    javaGrVars.test()
                    nodeGrVars.test()
                } 
            }
        
        
        }
     }
}
