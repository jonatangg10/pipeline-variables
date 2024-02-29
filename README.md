<p align="center">¡ Bienvenido !</p>
<p align="center"><b>Ejemplo practico de Jenkins</b></p>
<p align="center"><a>Dessarrollo un <b>Pipeline</b> para un proceso de manejo de variables del build</b></a></p>
<p align="center"><b>Si se puede inmaginar, se puede programar</b></p>

pipeline {
    agent any
    
    environment {
        PATH = "/usr/local/bin:$PATH"
        MAVEN_HOME = tool 'Maven'
        JAVA_HOME = tool 'Java'
    }
    
    parameters {
        string(name: 'GIT_REPO', defaultValue: 'https://github.com/user/repo.git', description: 'URL del repositorio Git')
        choice(name: 'BUILD_ENV', choices: ['dev', 'qa', 'prod'], description: 'Entorno de construcción')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: params.GIT_REPO]]])
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        
        stage('Deploy to ${params.BUILD_ENV}') {
            when {
                expression { params.BUILD_ENV == 'qa' || params.BUILD_ENV == 'prod' }
            }
            steps {
                script {
                    if (params.BUILD_ENV == 'qa') {
                        sh 'ansible-playbook -i hosts qa-deploy.yml'
                    } else {
                        sh 'ansible-playbook -i hosts prod-deploy.yml'
                    }
                }
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
        
        success {
            mail to: 'devops-team@example.com',
                 subject: "Pipeline successful: ${params.BUILD_ENV}",
                 body: "El pipeline para el entorno ${params.BUILD_ENV} se ejecutó exitosamente.",
                 from: 'jenkins@example.com'
        }
        
        failure {
            mail to: 'devops-team@example.com',
                 subject: "Pipeline failed: ${params.BUILD_ENV}",
                 body: "El pipeline para el entorno ${params.BUILD_ENV} ha fallado.",
                 from: 'jenkins@example.com'
        }
    }
}
