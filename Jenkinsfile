pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                // Code is automatically checked out in declarative pipeline
            }
        }
        
        stage('Hello World') {
            steps {
                echo 'Hello World from Jenkins Pipeline!'
                echo 'This pipeline is running from GitHub repository'
                // You can also run shell commands
                sh 'echo "Hello from shell command"'
                sh 'pwd'
                sh 'ls -la'
            }
        }
        
        stage('Environment Info') {
            steps {
                echo 'Displaying environment information...'
                sh 'whoami'
                sh 'date'
                sh 'uname -a'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed!'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
