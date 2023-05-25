pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/mbensalem1/devopsProject.git',
                credentialsId: '18469d85-eff5-45bb-a21b-b62c219a4e5a'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn  clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
