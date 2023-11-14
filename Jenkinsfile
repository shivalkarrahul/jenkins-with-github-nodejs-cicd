pipeline {
    agent any
    environment {
        IMAGE_TAG="${env.BUILD_ID}"
    }
   
    stages {

    // Tests
    stage('Unit Tests') {
      steps{
        script {
          sh 'npm install'
	  sh 'npm test -- --watchAll=false'
        }
      }
    }
        
    // Building Docker images
    stage('Building image') {
      steps{
        script {
          sh 'docker build -t sample_nodejs_application:${IMAGE_TAG}'
        }
      }
    }
   
    stage('Deploy') {
     steps{
        script {
          sh 'docker run sample_nodejs_application:${IMAGE_TAG}'
        }         
        }
      }      
      
    }
}

