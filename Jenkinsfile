pipeline {
    agent any

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
                sh '''
                    wget https://github.com/bandivenkatesh/spring-petclinic-own.git
                    cd spring-petclinic-own
                '''
            }
        }
    }
}
// this is a practise pipeline
// updating for trigerring build in jenkins
