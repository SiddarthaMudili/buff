pipeline {
    agent { 
        node {
            label 'docker-agent-python3'
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
                python3
                apt install python3-fire
                exit
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                python3 hello.py
                python3 hello.py --name=NoName
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff..>:D"
                '''
            }
        }
    }
}
