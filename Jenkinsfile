pipeline {
  agent any
  environment {
    NEW_VERSION = '1.3.0'
    GITHUB_CRED = credentials('f3c1a5d7-dc8a-4dda-88e4-aac3f4347f4f')
  }
  stages {
    stage("build") {
      steps {
        echo "building the application for prod"
        echo "build with creds ${GITHUB_CRED}"
        // nodejs wrapper
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
        echo "testing version ${NEW_VERSION}" // should be in double quotes only to interrogate the var as string
        // gradle wrapper
        /*withGradle() {
          // sh './gradlew -v'
        }*/
      }
    }
    stage("deploy") {
      // wants to run deploy stage only when branch name is either dev or main
      // conditional for this stage
      when {
          expression {
            BRANCH_NAME == 'dev' || BRANCH_NAME == 'main' // can use env.BRANCH_NAME as well
          }
      }
      steps {
        echo "deploying the application on prod"
        withCredentials([
          usernamePassword(credentials: 'f3c1a5d7-dc8a-4dda-88e4-aac3f4347f4f', usernameVariable: USER, passwordVariable: PWD)
        ]) {
          echo "user ${USER} password ${PWD}"
        }
      }
    }
  }
  // execute some logic after all stages executed
  post {
    always {
      echo "always"
    }
    failure {
      echo "failure"
    }
    success {
      echo "success"
      // execute when all stages gets build successfully
    }
  }
}
