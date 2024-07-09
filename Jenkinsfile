pipeline {
  agent any

  options {
        timeout(time: 10, unit: 'MINUTES') // Adjust the timeout as needed
    }
  stages {
    stage('compile voting app') {
      steps {
        echo 'compiling the voting app'
        dir(path: 'voting') {
          sh 'mvn compile'
        }

      }
    }

    stage('test voting') {
      steps {
        dir(path: 'voting') {
          sh 'mvn clean test'
        }

      }
    }

  }
  tools {
    maven 'maven'
  }
  post {
    always {
      echo 'completed pipeline for multistage app'
    }

  }
  options {
    timeout(time: 10, unit: 'MINUTES')
  }
}
