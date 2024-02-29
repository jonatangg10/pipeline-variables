<p align="center">¡ Bienvenido !</p>
<p align="center"><b>Ejemplo practico de Jenkins</b></p>
<p align="center"><a>Dessarrollo un <b>Pipeline</b> para un proceso de manejo de variables del build</b></a></p>
<p align="center"><b>Si se puede inmaginar, se puede programar</b></p>

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compilando el código...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Desplegando la aplicación...'
            }
        }
        stage('Confirmation') {
            steps {
                input message: '¿Deseas continuar con el despliegue?', ok: 'Deploy'
            }
        }
        stage('Finalize') {
            steps {
                echo 'Finalizando el despliegue...'
            }
        }
    }
}

