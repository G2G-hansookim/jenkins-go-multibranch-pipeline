pipeline {
   agent any

    tools {
        go 'go-1.17.3'
    }

    environment {
        GO111MODULE = 'auto'
        GITHUB_TOKEN = credentials('github_credentials')
    }

    stages {
        stage('PreBuild') {
            steps {
                echo "prebuild"
                bat 'go version'
            }
        }

        stage('Build & Unit Test') {
            steps {
                echo "start build"

                // Build
                bat 'go build'

                echo "start unit test"

                // Remove cached test results.
                bat 'go clean -cache'

                // Run Unit Tests.
                bat 'go test ./... -coverprofile=report.txt'
            }
        }

        stage('Results') {
            steps {
                echo "results"

                // go test results
                archiveArtifacts artifacts: "report.txt", fingerprint: true

                // go build results
                archiveArtifacts artifacts: "*.exe", fingerprint: true, onlyIfSuccessful: true
            }
        }

        stage('Static Code Analytics') {
            steps {
               echo "static code analytics"
            }
        }

        stage('Integration Test') {
            steps {
                echo "integration test"
            }
        }

        stage ('Publish') {
              steps {
                   echo "publish"
              }
        }
    }
}