pipeline {
   agent any

    tools {
        go 'go-1.17.3'
    }

    environment {
        GO111MODULE = 'on'
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
                echo "Success Build!"
            }
        }

        stage('Result') {
            steps {
                bat "Result!"
            }
        }
    }
}