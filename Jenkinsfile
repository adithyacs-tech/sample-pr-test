pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // your actual build/test steps here
            }
        }
    }

    post {
        success {
            githubNotify context: 'CI/Jenkins', status: 'SUCCESS', description: 'Build succeeded'
        }
        failure {
            githubNotify context: 'CI/Jenkins', status: 'FAILURE', description: 'Build failed'
        }
    }
}
