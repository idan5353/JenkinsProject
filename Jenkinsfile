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
        echo 'Deploying app... (skipped for now)'
        // For example, you can add docker build/push or AWS deploy here
      }
    }
  }
}
