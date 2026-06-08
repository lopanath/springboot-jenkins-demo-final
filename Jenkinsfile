pipeline {
    agent { 
        node {
            label 'docker-agent-java-git-maven'
            }
      }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                    mvn clean compile
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                mvn test
                '''
            }
        }
         stage('Package') {
                    steps {
                        echo "creating jar file.."
                        sh '''
                        mvn clean package
                        '''
                    }
                }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                ls -l target/
                '''
            }
        }
    }
}
