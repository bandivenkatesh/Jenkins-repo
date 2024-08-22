pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'M3' // Adjust to your Maven installation
        JAVA_HOME = tool 'JDK17' // Adjust to your JDK installation
    }

    stages {
        stage('Fetch Data/Code from Repository') {
            steps {
                git 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }

        stage('Environment Setup') {
            steps {
                script {
                    // No specific setup needed for Maven projects
                }
            }
        }

        stage('Static Code Analysis') {
            steps {
                script {
                    // Run Maven's checkstyle or PMD plugin
                    sh './mvnw checkstyle:check'
                }
            }
        }

        stage('Unit Testing') {
            steps {
                script {
                    sh './mvnw test'
                }
            }
        }

        stage('Code Linting and Formatting') {
            steps {
                script {
                    // Use Spotless or similar for formatting
                    sh './mvnw spotless:apply'
                }
            }
        }

        stage('Integration Testing') {
            steps {
                script {
                    // Run integration tests
                    sh './mvnw verify -Pintegration'
                }
            }
        }

        stage('Build and Compile') {
            steps {
                script {
                    sh './mvnw package'
                }
            }
        }

        stage('Code Coverage Analysis') {
            steps {
                script {
                    sh './mvnw jacoco:report'
                }
            }
        }

        stage('Deployment to Staging Environment') {
            steps {
                script {
                    // Deploy using Docker Compose
                    sh 'docker-compose --profile mysql up -d'
                }
            }
        }

        stage('Automated UI Testing') {
            steps {
                script {
                    // Placeholder for UI testing
                    echo 'Run UI tests with Selenium or similar'
                }
            }
        }

        stage('Generate Documentation') {
            steps {
                script {
                    sh './mvnw javadoc:javadoc'
                }
            }
        }

        stage('Performance Testing') {
            steps {
                script {
                    // Placeholder for performance testing
                    echo 'Run performance tests with JMeter or similar'
                }
            }
        }

        stage('Security Scanning') {
            steps {
                script {
                    // Placeholder for security scanning
                    echo 'Run security scans with OWASP ZAP or similar'
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            junit 'target/surefire-reports/*.xml'
        }
    }
}