pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Compilar y Empaquetar') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }
        
        stage('Ejecutar Tests') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
                }
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completado'
        }
        success {
            echo 'Pipeline ejecutado con éxito'
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
        failure {
            echo 'Pipeline falló'
        }
    }
}