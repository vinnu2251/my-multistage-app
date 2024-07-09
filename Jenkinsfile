pipeline {
  agent any

   environment {
        DOCKER_CREDENTIALS_ID = 'docker-cred' // ID of the Docker Hub credentials in Jenkins
        DOCKER_IMAGE_NAME = 'vinay7944/my-multitier-app-voting'
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

    stage('packaging voting'){
      steps{
        dir(path: 'voting') {
          sh 'mvn package -DskipTests'
        }

        archiveArtifacts(artifacts: '**/target/*.jar')

      }
    }

    stage('Build') {
            steps {
                echo 'Building Docker image'
                script {
                    // Build the Docker image specifying the path to the Dockerfile
                    docker.build("${env.DOCKER_IMAGE_NAME}:latest", "./voting")
                }
            }
        }

    stage('Push') {
            steps {
                echo 'Pushing Docker image to Docker Hub'
                script {
                    // Login to Docker Hub
                    docker.withRegistry('https://index.docker.io/v1/', "${env.DOCKER_CREDENTIALS_ID}") {
                        // Push the Docker image
                        docker.image("${env.DOCKER_IMAGE_NAME}:latest").push()
                    }
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
}
