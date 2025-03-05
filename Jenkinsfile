pipeline {
    agent any
    // tools {
    //     maven 'Maven 3'
    // }
    environment {
        SONAR_URL = 'http://35.211.186.41:9000'
        SONAR_TOKEN = credentials('sonar-token')  // Add this in Jenkins credentials
    }
    stages {
        /*
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Saicharan619/devops-1sonarqube.git'
            }
        }
        */
        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                sh '''
                mvn sonar:sonar \
                    -Dsonar.projectKey=my-project \
                    -Dsonar.host.url=${SONAR_URL} \
                    -Dsonar.token=${SONAR_TOKEN}
                '''
            }
        }
    /*     stage('Check Quality Gate') {
            steps {
                script {
                    timeout(time: 2, unit: 'MINUTES') {
                        def qualityGate = waitForQualityGate()
                        if (qualityGate.status != 'OK') {
                            error "❌ Quality Gate failed! Code coverage must be greater than 70%."
                        }
                    }
                }
            }
        } */
    }
}
