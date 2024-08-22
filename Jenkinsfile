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
        stage('Clone Repository') {
            steps {
                script {
                    git 'https://github.com/bandivenkatesh/spring-petclinic-own.git'
                }
            }
        }
        stage('Build Java Application') {
            steps {
                script {
                    dir('spring-petclinic-own') {
                        sh 'mvn clean package'
                    }
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    dir('spring-petclinic-own') {
                        sh 'mvn test'
                    }
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dir('spring-petclinic-own') {
                        docker.build("${imageName}:${imageTag}")
                    }
                }
            }
        }
        stage('Clean Up') {
            steps {
                echo 'Cleaning up workspace...'
                cleanWs()
            }
        }
    }
}