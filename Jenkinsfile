pipeline {
  agent any
  stages {
    stage("build") {
      steps {
        echo "building the application for prod"
        nodejs('Node10.17') {
          sh 'npm install'
          sh 'yarn install'
          sh 'yarn -v'
        }
      }
    }
    stage("test") {
      steps {
        echo "testing the application"
        withGradle() {
          sh './gradlew -v'
        }
      }
    }
    stage("deploy") {
      steps {
        echo "deploying the application on prod"
      }
    }
  }
}
