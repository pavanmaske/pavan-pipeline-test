pipeline {
    agent any
    environment {
        MAVEN_HOME = '/usr/share/maven' // Path to Maven installation
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master', url: 'https://github.com/pavanmaske/pavan-pipeline-test.git'
            }
        }
        stage('Build with Maven') {
            steps {
                sh "${MAVEN_HOME}/bin/mvn clean package"
            }
        }
        stage('Run Unit Tests') {
            steps {
                sh "${MAVEN_HOME}/bin/mvn test"
            }
        }
    }
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
