<p align="center">¡ Bienvenido !</p>
<p align="center"><b>Ejemplo practico de Jenkins</b></p>
<p align="center"><a>Dessarrollo un <b>Pipeline</b> para un proceso de manejo de variables del build</b></a></p>
<p align="center"><b>Si se puede inmaginar, se puede programar</b></p>

pipeline {
    agent any
    parameters {
        choice(name: 'Entorno', choices: ['Desarrollo', 'Producción', 'Pruebas'], description: 'Seleccione el entorno de implementación')
    }
    stages {
        stage('Configuración') {
            steps {
                script {
                    echo "Entorno seleccionado: ${params.Entorno}"
                }
            }
        }
        // Agrega más etapas según sea necesario
    }
}
