pipeline {
    agent any

    stages {
        stage('Compilar') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Pruebas') {
            steps {
                bat 'mvn test'
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}
