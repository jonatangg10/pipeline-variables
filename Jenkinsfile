pipeline {
    agent any
    environment {
        LANG = 'es_CO.UTF-8'
        LANGUAGE = 'es_CO:es'
    }
    stages {
        stage('Build') { 
            steps {
                echo pwd
            }
        }
        stage('Test') { 
            steps {
                echo 'Arranca el proceso de pruebas unitarias' 
            }
        }
        stage('Deploy') { 
            steps {
                echo 'Desplegando al área de desarrollo' 
            }
        }
    }
    post {
        always {
            script {
                echo "Jenkins URL: ${BUILD_URL}"
                echo "Notificación de Jenkins: ${currentBuild.fullDisplayName}"
                echo "Número de Build: ${currentBuild.number}"
                echo "Resultado del Build: ${currentBuild.result}"
                echo "Tiempo de inicio: ${new Date(currentBuild.startTimeInMillis)}"
                def duracion = currentBuild.duration / 1000.0
                echo "Duración del Build: ${duracion} segundos"    
                // Prueba  
                // echo "${JOB_NAME}"
                echo "${WORKSPACE}"
                echo "${JOB_NAME}"
               
            } 
        }
    }
}
