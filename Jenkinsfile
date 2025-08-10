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
        echo 'Building the app...'
        // Add build steps here
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        // Add test steps
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying...'
        // Docker, EKS, SCP, etc.
      }
    }
  }
}
