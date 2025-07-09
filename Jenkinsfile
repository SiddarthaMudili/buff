pipeline {
    agent any
    
    stages {
        stage('Checkout from GitHub') {
            steps {
                echo 'Checking out code from GitHub repository...'
                git branch: 'main', 
                    url: 'https://github.com/yourusername/your-repo.git'
            }
        }
        
        stage('Hello World') {
            steps {
                echo 'Hello World from Jenkins!'
                echo 'Successfully pulled code from GitHub'
                
                // Display repository contents
                sh 'echo "Repository contents:"'
                sh 'ls -la'
                
                // If you have a specific file in your repo
                script {
                    if (fileExists('README.md')) {
                        sh 'echo "README.md exists!"'
                        sh 'head -5 README.md'
                    }
                }
            }
        }
        
        stage('Run Custom Script') {
            steps {
                echo 'Running custom commands...'
                
                // If you have a script in your repository
                script {
                    if (fileExists('hello.sh')) {
                        sh 'chmod +x hello.sh'
                        sh './hello.sh'
                    } else {
                        echo 'No hello.sh script found, creating one...'
                        sh '''
                            echo "#!/bin/bash" > hello.sh
                            echo "echo 'Hello World from custom script!'" >> hello.sh
                            chmod +x hello.sh
                            ./hello.sh
                        '''
                    }
                }
            }
        }
    }
    
    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
