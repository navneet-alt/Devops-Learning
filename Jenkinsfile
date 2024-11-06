pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from your version control system
                git url: 'https://github.com/navneet-alt/Devops-Learning', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Upgrade pip and install dependencies globally
                    bat '''
                        python -m pip install --upgrade pip
                    '''
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run tests using unittest
                    bat 'python test_calculator.py'
                }
            }
        }
    }

    post {
        always {
            // Clean up the workspace after the build
            cleanWs()
        }
        success {
            echo 'Tests passed successfully!'
        }
        failure {
            echo 'Tests failed!'
        }
    }
}
