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
                bat 'go test ./... -v -short'
            }
        }

        stage('Results') {
            steps {
                echo "results"
                archiveArtifacts artifacts: "target/*.exe", fingerprint: true, onlyIfSuccessful: true
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
//               when {
//                 buildingTag()
//               }

              steps {
//                 bat 'curl -sL https://git.io/goreleaser | bash'

                   echo "publish"

//                    Find out current branch
//                    bat 'git name-rev --name-only HEAD > GIT_BRANCH'
//                    def branch = readFile('GIT_BRANCH').trim()
//
//                     //strip off repo-name/origin/ (optional)
//                     branch = branch.substring(branch.lastIndexOf('/') + 1)
//
//                     def archive = "${GOPATH}/project-${branch}-${commit}.tar.gz"
//
//                     echo "building archive ${archive}"

//                     bat """tar -cvzf ${archive} $GOPATH/src/cmd/project/project"""
//
//                     echo "uploading ${archive}"
//                     withCredentials([string(credentialsId: 'bb-upload-key', variable: 'KEY')]) {
//                     bat """curl -s -u 'user:${KEY}' -X POST 'downloads-page-url' --form files=@'${archive}' --fail"""


              }
            }
    }
}