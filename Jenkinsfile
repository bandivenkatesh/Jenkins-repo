pipeline {
    agent any

    environment {
        imageName = "pet-clinic"
        imageTag = "v1"
    }

    stages {
        stage('step-one') {
            steps {
                echo 'Hello-World'
            }
        }
        stage('step-two') {
            steps {
                sh 'hostname'
            }
        }
        stage('step-three') {
            steps {
                script {
                    // Clone the repository
                    git 'https://github.com/bandivenkatesh/spring-petclinic-own.git'

                    // Change directory to the cloned repository
                    dir('spring-petclinic-own') {
                        // Build the Java application using Maven
                        sh 'mvn clean package'

                        // Build the Docker image with a specific name and tag
                        docker.build("${imageName}:${imageTag}")
                    }
                }
            }
        }
    }
}
// this is a practise pipeline
// updating for trigerring build in jenkins
