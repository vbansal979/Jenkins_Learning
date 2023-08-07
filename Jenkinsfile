pipeline {
  agent any
  stages {
    stage("build") {
      steps {
        echo "building the application for production env"
        withGradle() {
          sh './gradle -v'
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
