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

    post {
      failure {
        slackSend failOnError:true, message:"Build failed  - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
      }
    }

}
