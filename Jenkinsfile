// I configured this shared library in Jenkins using JCasC plugin writing config files
@Library('sms-library') _

pipeline {

    agent any

    environment {
        DOCKER_USERNAME = "ashirqayyum"
        FRONTEND_IMAGE = "ashirqayyum/sms-frontend"
        BACKEND_IMAGE  = "ashirqayyum/sms-backend"
        IMAGE_TAG = "jenkins"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Docker Login') {
            steps {
                dockerLogin()
            }
        }

        stage('Build Backend Image') {
            steps {
                buildBackend()
            }
        }

        stage('Build Frontend Image') {
            steps {
                buildFrontend()
            }
        }

        stage('Push Backend Image') {
            steps {
                pushBackend()
            }
        }

        stage('Push Frontend Image') {
            steps {
                pushFrontend()
            }
        }

        stage('Deploy PostgreSQL') {
            steps {
                deployPostgres()
            }
        }

        stage('Deploy Backend') {
            steps {
                deployBackend()
            }
        }

        stage('Deploy Frontend') {
            steps {
                deployFrontend()
            }
        }

    }

}