pipeline {
   agent any

    tools {
        go 'go-1.17.3'
    }

    environment {
        GO111MODULE = 'on'
        GOPATH = "D:/jenkins-go-multibranch-pipeline"
    }

    stages {
        stage('PreBuild') {
            steps {
                bat 'go version'
            }
        }

        stage('Build') {
            steps {
                 bat """cd $GOPATH/ && go build"""
            }
        }

        stage('Result') {
            steps {
                echo "Result!"
            }
        }
    }
}