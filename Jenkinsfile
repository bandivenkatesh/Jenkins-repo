pipeline {
    agent any

    stages {
        stage('step-one') {
            steps {
                echo 'Hello-World'
            }
        }
        stage ('step-two') {
             steps {
              hostname
            }
          stage ('step-three') {
              steps {
                wget https://github.com/bandivenkatesh/spring-petclinic-own.git
                cd spring-petclinic-own
              }
          }
        }
    }
}