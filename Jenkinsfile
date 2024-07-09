pipeline {
    agent any

    tools{
        maven 'maven'
    }

    stages {
        stage('Build voting app') {
            steps {
                echo 'compiling the voting app'
                dir(path: 'voting'){
                        sh 'mvn compile'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }

    post{
        always {
            echo 'completed pipeline for multistage app'
        }
    }
}
