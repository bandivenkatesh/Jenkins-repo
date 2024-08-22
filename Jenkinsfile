pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'M3' // Ensure this matches your Maven installation name
        JAVA_HOME = tool 'JDK17' // Ensure this matches your JDK installation name
    }

    stages {
        stage('Fetch Data/Code from Repository') {
            steps {
                git 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }

        stage('Environment Setup') {
            steps {
                echo 'Environment setup complete'
            }
        }

        stage('Static Code Analysis') {
            steps {
                sh './mvnw checkstyle:check'
            }
        }

        stage('Unit Testing') {
            steps {
                sh './mvnw test'
            }
        }

        stage('Code Linting and Formatting') {
            steps {
                sh './mvnw spotless:apply'
            }
        }

        stage('Integration Testing') {
            steps {
                sh './mvnw verify -Pintegration'
            }
        }

        stage('Build and Compile') {
            steps {
                sh './mvnw package'
            }
        }

        stage('Code Coverage Analysis') {
            steps {
                sh './mvnw jacoco:report'
            }
        }

        stage('Deployment to Staging Environment') {
            steps {
                sh 'docker-compose up -d'
            }
        }

        stage('Automated UI Testing') {
            steps {
                echo 'Run UI tests with Selenium or similar'
            }
        }

        stage('Generate Documentation') {
            steps {
                sh './mvnw javadoc:javadoc'
            }
        }

        stage('Performance Testing') {
            steps {
                echo 'Run performance tests with JMeter or similar'
            }
        }

        stage('Security Scanning') {
            steps {
                echo 'Run security scans with OWASP ZAP or similar'
            }
        }
    }

    post {
        always {
            node {
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}
