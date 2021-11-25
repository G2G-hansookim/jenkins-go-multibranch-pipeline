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

        stage ('Deploy') {
//               when {
//                 buildingTag()
//               }

              environment {
                GITHUB_TOKEN = credentials('github_credentials')
              }

              steps {
                bat 'curl -sL https://git.io/goreleaser | bash'
              }
            }
    }
}