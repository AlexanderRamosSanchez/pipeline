pipeline {
    agent any
    tools {
        maven 'Maven_3.8.6' // Asegúrate de tener Maven configurado en
        Jenkins
        jdk 'Java_17' // Asegúrate de tener Java 17 configurado

        en Jenkins
    }
    stages {
        stage('Clonar Repositorio') {
            steps {
                echo 'Clonando repositorio...'
            }
        }
        stage('Compilar Proyecto') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Ejecutar Pruebas') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Construir Artefacto') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Finalizar') {
            steps {
                echo '¡Pipeline completado correctamente!'
            }
        }
    }
    post {
        success {
            echo '✅ Éxito: todo funcionó.'
        }
        failure {
            echo '❌ Fallo: algo salió mal.'
        }
    }
}