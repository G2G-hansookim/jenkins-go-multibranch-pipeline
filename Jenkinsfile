pipeline {
   agent any

    tools {
        go 'go-1.17.3'
    }

    environment {
        GO111MODULE = 'on'
    }

    stage('PreBuild') {
        sh 'go version'
    }
}