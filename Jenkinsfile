pipeline {
    agent any

    tools{
        maven 'maven'
    }

    stages {
        stage('compile voting app') {
            steps {
                echo 'compiling the voting app'
                dir(path: 'voting'){
                        sh 'mvn compile'
                }
            }
        }
        
    }

    post{
        always {
            echo 'completed pipeline for multistage app'
        }
    }
}
