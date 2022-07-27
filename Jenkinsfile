pipeline {
  agent any
  tools {nodejs "NodeJs"}
  stages {       
    stage('Git') {
      steps {
        slackSend color: "good", message: "Started build, fetching repo from github"
        git 'https://github.com/Sateesh2/simple-node-js-react-npm-app.git'
      }
    }
     
    stage('Build') {
      steps {
        script {
          try {
            sh 'npm install'
          } catch (Exception e) {
              slackSend failOnError:true,color: "#ff0000", message:"npm install failed ${e.toString()} - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
          }
        }
        sh 'npm run build'
      }
    }  
  }

    post {
      failure {
        slackSend failOnError:true,color: "#ff0000", message:"Build failed  - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
      }
    }

}
