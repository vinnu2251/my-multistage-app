pipeline {
  agent any


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

    stage('packaging voting'){
      steps{
        dir(path: 'voting') {
          sh 'mvn package -DskipTests'
        }

        archiveArtifacts(artifacts: '**/target/*.jar')

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
}
