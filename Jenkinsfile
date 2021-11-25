pipeline {
   agent any

    tools {
        go 'go-1.17.3'
    }

    environment {
        GO111MODULE = 'auto'
    }

    stages {
        stage('PreBuild') {
            steps {
                bat 'go version'
            }
        }

        stage('Build') {
            steps {
                bat 'go build'
            }
        }

        stage ('Release') {
              when {
                buildingTag()
              }

              environment {
                GITHUB_TOKEN = credentials('github_credentials')
              }

              steps {
                bat 'curl -sL https://github.com/G2G-hansookim/jenkins-go-multibranch-pipeline.git | bash'
              }
            }
    }
}