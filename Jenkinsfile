pipeline {
  agent any

  environment {
    BRANCH_NAME = "${env.GIT_BRANCH}".replaceFirst(/^origin\//, '')
  }

  stages {
    stage('Init') {
      steps {
        echo "🚀 Starter pipeline for branch: ${BRANCH_NAME}"
      }
    }

    stage('Bygg') {
      steps {
        echo "🔨 Bygger prosjekt..."
      }
    }

    stage('Test') {
      steps {
        echo "🧪 Kjører tester..."
      }
    }

    stage('Deploy') {
      when {
        anyOf {
          branch 'main'
          branch 'develop'
        }
      }
      steps {
        script {
          if (env.BRANCH_NAME == "main") {
            echo "🚀 Deploy til PRODUKSJON!"
            // her kan du legge inn kommando for produksjonsdeploy
          } else if (env.BRANCH_NAME == "develop") {
            echo "🚧 Deploy til STAGING!"
            // her kan du legge inn staging-deploy
          } else {
            echo "❌ Ukjent branch. Ingen deploy utføres."
          }
        }
      }
    }
  }
}
