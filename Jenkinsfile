pipeline {
  agent any
  stages {
    stage('checkout code') {
      parallel {
        stage('checkout code') {
          steps {
            git(url: 'git@github.com:sagidevops/NodeJS-EmptySiteTemplate.git', branch: 'master', credentialsId: 'Github-creds')
          }
        }

        stage('Say Hello') {
          steps {
            sh 'echo "Hello"'
          }
        }

      }
    }

    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

  }
}