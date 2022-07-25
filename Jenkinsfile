pipeline {
  agent any
  stages {
    stage('checkout code') {
      parallel {
        stage('checkout code') {
          steps {
            cleanWs()
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

    stage('Test App') {
      parallel {
        stage('Run The App') {
          steps {
            sh 'node server.js'
          }
        }

        stage('check if app is running') {
          steps {
            sh '''sleep 5
curl localhost:8081
if [ $?(echo $?) -eq 0 ];
then
  echo "success"
  ps -ef | grep node | awk \'{print $2}\' | head -n 1 | xargs kill
  exit 0
else
  echo "failure"
  exit 1
fi'''
          }
        }

      }
    }

  }
}