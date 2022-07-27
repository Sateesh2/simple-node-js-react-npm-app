pipeline {
  agent any
  stages {       
    stage('Git') {
      steps {
        slackSend color: "good", message: "Message from Jenkins Pipeline"
        git 'https://github.com/Sateesh2/simple-node-js-react-npm-app.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
         sh 'npm run build'
      }
    }  
    
            
    stage('Test') {
      steps {
        sh 'node test'
      }
    }
  }
}
