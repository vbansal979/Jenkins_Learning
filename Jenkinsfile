pipeline {
  agent any
  stages {
    stage("build") {
      steps {
        echo "building the application for prod"
        NodeJS('Node20.5') {
          sh 'npm install'
          sh 'yarn install'
          sh 'yarn -v'
        }
      }
    }
    stage("test") {
      steps {
        echo "testing the application"
      }
    }
    stage("deploy") {
      steps {
        echo "deploying the application on prod"
      }
    }
  }
}
