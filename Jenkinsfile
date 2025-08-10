pipeline {
  agent any

  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'git@github.com:<your-username>/<repo>.git'
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
