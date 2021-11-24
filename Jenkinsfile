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
                sh 'go version'
            }
        }

        stage('Build') {
            steps {
                sh 'go build'
                echo "Success Build!"
            }
        }

        stage('Result') {
            steps {
                echo "Result!"
            }
        }
    }
}