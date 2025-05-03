pipeline {
    agent any
    
    // Eliminamos la sección tools ya que causa el error
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Compilar y Empaquetar') {
            steps {
                // Usamos mvn o mvn.cmd según el sistema operativo
                sh 'mvn clean package -DskipTests'
            }
        }
        
        stage('Ejecutar Tests') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
                }
            }
        }
        
        // Opcional: añadir si tienes tests de integración configurados
        /* 
        stage('Pruebas de Integración') {
            steps {
                sh 'mvn verify -Dskip.unit.tests=true'
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: '**/target/failsafe-reports/*.xml'
                }
            }
        }
        */
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