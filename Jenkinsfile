pipeline {
    agent any
    stages {
    stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/mbensalem1/devopsProject.git',
                credentialsId: 'github_creds'
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

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
        
         stage('Sonar') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.username=admin -Dsonar.password=admin'
            }      
        }
        
        stage('Deploy') {
            steps {
                        nexusArtifactUploader(
                            nexusVersion: 'nexus3',
                            protocol: 'http',
                            nexusUrl: 'http://localhost:8081/repository/devops/',
                            version: '1.0.0',
                            repository: 'devops',
                            credentialsId: 'nexus_creds',
                            artifacts: [
                                [artifactId: 'ExamThourayaS2',
                                 classifier: '',
                                 file: 'target/ExamThourayaS2-1.0.jar',
                                 type: 'jar']
                            ]
                         )
            }
        }
        

    }
}
