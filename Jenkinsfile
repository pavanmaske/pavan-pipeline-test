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
        stage('Build and SonarQube') {
            steps {
                sh "${MAVEN_HOME}/bin/mvn clean verify sonar:sonar -Dsonar.host.url=http://http://13.239.237.99:9000/ -Dsonar.login=sqa_4a48cb83280e404c0ee46355bde6085fbc8ebfa4"
            }
        }
        stage('Run Unit Tests') {
            steps {
                // Optional: You can remove this if tests are also included in the previous mvn command
                // or keep it separately if needed
                sh "${MAVEN_HOME}/bin/mvn test"
            }
        }
    }
    post {
        success {
            echo 'Build and analysis successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
