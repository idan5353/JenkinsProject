pipeline {
  agent any

  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/idan5353/JenkinsProject.git'
      }
    }

    stage('Build') {
      steps {
        echo 'Installing dependencies...'
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        sh 'npm test'
      }
    }

    stage('Deploy') {
      steps {
        sshagent(['jenkins-ssh-credentials-id']) {
          sh '''
            ssh -o StrictHostKeyChecking=no ubuntu@<app-server-public-ip> << EOF
              cd JenkinsProject || git clone https://github.com/idan5353/JenkinsProject.git JenkinsProject && cd JenkinsProject
              git pull origin main
              npm install
              pm2 restart simple-app || pm2 start index.js --name simple-app
            EOF
          '''
        }
      }
    }
  } // close stages

} // close pipeline
