<p align="center">¡ Bienvenido !</p>
<p align="center"><b>Ejemplo practico de Jenkins</b></p>
<p align="center"><a>Dessarrollo un <b>Pipeline</b> para un proceso de manejo de variables del build</b></a></p>
<p align="center"><b>Si se puede inmaginar, se puede programar</b></p>

pipeline {
    agent any

    stages {
        stage('Input') {
            steps {
                script {
                    def userInput = input(
                        id: 'userInput', message: 'Por favor ingrese su nombre:',
                        parameters: [
                            string(defaultValue: 'Anónimo', description: 'Nombre del usuario', name: 'Nombre')
                        ]
                    )
                    echo "Hola, ${userInput.Nombre}!"
                }
            }
        }
    }
}


