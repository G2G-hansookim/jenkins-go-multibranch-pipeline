pipeline {
   agent any

    tools {
        go 'go-1.17.3'
    }

    environment {
        GO111MODULE = 'on'
        GOPATH = '${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_ID}'
    }

    stages {
        stage('PreBuild') {
            steps {
                bat 'go version'
            }
        }

        stage('Build') {
            steps {
                 bat """cd $GOPATH/ && go build -ldflags '-s'"""
            }
        }

        stage('Result') {
            steps {
                echo "Result!"
            }
        }
    }
}