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
          mail to: 'navneetkumar142000@gmail.com',                
               subject: "Jenkins Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",                  
               body: "Good news! The Jenkins build for job ${env.JOB_NAME} #${env.BUILD_NUMBER} completed successfully.\nCheck it at ${env.BUILD_URL}"         
         }
        failure {
            mail to: 'navneetkumar142000@gmail.com',
                subject: "Jenkins Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Unfortunately, the Jenkins build for job ${env.JOB_NAME} #${env.BUILD_NUMBER} failed.\nCheck it at ${env.BUILD_URL}"
        }
    }
}

