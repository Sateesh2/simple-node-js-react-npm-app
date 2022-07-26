pipeline {
  agent any
    
  tools {NodeJs "node"}
    
  stages {
        
    stage('Git') {
      steps {
        git 'https://github.com/Sateesh2/simple-node-js-react-npm-app.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
         sh 'npm build'
      }
    }  
    
            
    stage('Test') {
      steps {
        sh 'node test'
      }
    }
  }
post {
    failure {
        slackSend failOnError:true message:"Build failed  - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
    }
}
}
