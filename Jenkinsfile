pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the GitHub repository containing the registration form project
                git branch: 'main', url: 'https://github.com/username/registration-form-repo'
            }
        }
        
        stage('HTML Linting') {
            steps {
                script {
                    // Lint the HTML file using htmlhint
                    // Assumes htmlhint is installed on the Jenkins node
                    def htmlLintResult = sh(script: 'htmlhint index.html --config .htmlhintrc', returnStatus: true)
                    if (htmlLintResult != 0) {
                        error "HTML Linting failed!"
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully! HTML validation passed.'
        }
        failure {
            echo 'Pipeline failed during HTML validation. Check console output for errors.'
        }
    }
}
