pipeline {
    agent any
 environment {
        MAVEN_HOME = tool 'jenkins-maven' // Set this in Jenkins tools config
        DOCKER_IMAGE = 'multiservice-image'
        CONTAINER_NAME = 'multiservice-container'
    }
    stages {
        stage('Checkout') {
            steps {
           git branch: 'main', url: 'https://github.com/Ranjana0123/MultiServiceDockerApp'
            }
        }

        stage('Build with Maven') {
            steps {
                bat "${MAVEN_HOME}/bin/mvn clean install -DskipTests"
            }
        }

        stage('Docker Compose - Build') {
            steps {
                bat 'docker-compose build'
            }
        }

        stage('Docker Compose - Up') {
            steps {
                bat 'docker-compose up -d'
            }
        }
    }
}
