<p align="center">¡ Bienvenido !</p>
<p align="center"><b>Ejemplo practico de Jenkins</b></p>
<p align="center"><a>Dessarrollo un <b>Pipeline</b> para un proceso de manejo de variables del build</b></a></p>
<p align="center"><b>Si se puede inmaginar, se puede programar</b></p>

pipeline {
    agent any

    parameters {
        booleanParam(defaultValue: false, description: 'Seleccione "true" para habilitar la opción', name: 'opcion')
    }

    stages {
        stage('Ejecución') {
            steps {
                script {
                    if (params.opcion) {
                        echo 'La opción está habilitada.'
                    } else {
                        echo 'La opción está deshabilitada.'
                    }
                }
            }
        }
    }
}



