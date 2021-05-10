pipeline {

    agent any

    environment {
        SERVER = "192.168.0.2"
        FRONTEND_REPO = "abc"
    }

    stages {
        stage('Clone Repositories') {
            steps {
                dir ("${FRONTEND_REPO}") {
                    git (
                      url: 'git@github.com:{{ repo url }}',
                      credentialsId: 'jenkins-ci-creds',
                      branch: "master"
                    )
                }
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Generate'){
            steps {
                sh 'npm run generate'
            }
        }

        stage('Run') {
            steps {
                sh 'npm run server'
            }
        }
    }
}