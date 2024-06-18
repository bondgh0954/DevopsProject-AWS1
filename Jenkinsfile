pipeline {
  agent any
  tools {
    nodejs 'nodejs'
  }

  stages{
    stage('build jar'){
      steps{
        script{
          echo 'building jar file for application'
          sh 'npm build'
          sh 'npm pack'
        }
      }
    }

    stage('build image'){
      steps{
        script{
          echo 'building application as docker image ....'
          sh 'docker build -t nanaot/java-app:node1.1 .'
          withCredentials([usernamePassword(credentialsId:'dockerhub-credentials',usernameVariable:'USER',passwordVariable:'PASS')]){
             sh "echo $PASS |docker login -u $USER --password-stdin"
             sh 'docker push nanaot/java-app:node1.1'
          }
        }
      }
    }

    stage('deploy app'){
      steps{
        script{
          def dockerCmd = 'docker run -p 3080:3080 -d nanaot/java-app:node1.1'
          sshagent(['server-key']) {
            sh "ssh -o StrictHostKeyChecking=0 ec2-user@3.70.229.24 ${dockerCmd}"
          }
        }
      }
    }
  }
}
