pipeline {
    // Usamos un agente que tenga python3 y pip
    agent { docker { image 'python:3.9-slim' } }

    stages {
        stage('Build') {
            steps {
                echo 'Construyendo el proyecto...'
            }
        }
        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Instalando herramientas de seguridad...'
                // Instala las dependencias y la herramienta bandit
                sh 'pip install -r requirements.txt'

                echo 'Ejecutando análisis estático con Bandit...'
                // Ejecuta bandit en todo el código.
                // '|| true' previene que el pipeline falle si se encuentran vulnerabilidades, para solo obtener el reporte.
                sh 'bandit -r . || true'
            }
        }
    }
}