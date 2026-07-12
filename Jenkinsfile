pipeline {
  agent any

  environment {
    CF_API = "${env.CF_API}"
    CF_ORG = "${env.CF_ORG}"
    CF_SPACE = "${env.CF_SPACE}"
    CF_USERNAME = "${env.CF_USERNAME}"
    CF_PASSWORD = "${env.CF_PASSWORD}"
    CF_APP_NAME = "snake-game"
  }

  stages {
    stage('Build') {
      steps {
        echo 'Static application - no build step required.'
      }
    }

    stage('Deploy') {
      steps {
        sh '''#!/bin/bash
          set -e
          cf api "$CF_API"
          cf auth "$CF_USERNAME" "$CF_PASSWORD"
          cf target -o "$CF_ORG" -s "$CF_SPACE"
          cf push "$CF_APP_NAME" -f manifest.yml
        '''
      }
    }
  }
}
