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
//                 bat 'go get -u golang.org/x/lint/golint'
            }
        }

        stage('Build & Unit Test') {
            steps {
                echo "start build"
                timeout(time: 3, unit: 'MINUTES') {
                    retry(5) {
                        // Build
                        bat 'go build'
                    }
                }

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
                archiveArtifacts artifacts: "*.txt", fingerprint: true

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

    // When the Pipeline has finished executing, you may need to run clean-up steps or perform some actions based on the outcome of the Pipeline. These actions can be performed in the post section.
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}