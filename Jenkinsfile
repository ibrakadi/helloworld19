pipeline {
  agent any
  tools {
     maven 'M2_HOME'  
  }
  environment {
    registry = "ibrakadi/devop-pipeline"
    registryCredential = 'dockerID'  
  }
  stages {
    stage('Build'){
      steps {
       sh 'mvn clean'
       sh 'mvn install' 
       sh 'mvn package'
      }
    }
   stage('test'){
      steps {
       echo "test step"
       sh 'mvn test'
      }
    } 
 stage('Deploy'){
      steps {
       script {
        docker.build registry + ":$BUILD_NUMBER"
       }
     }
   }
 }
}
