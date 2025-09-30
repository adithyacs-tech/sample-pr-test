pipeline {
    agent any

    // Restrict pipeline execution only to PRs targeting "main"
    when {
        expression {
            return env.CHANGE_ID && env.CHANGE_TARGET == 'main'
        }
    }

    stages {
        stage('PR Details') {
            steps {
                script {
                    echo "Pull Request ID: ${env.CHANGE_ID ?: 'Not a PR'}"
                    echo "Source Branch: ${env.CHANGE_BRANCH ?: 'Not a PR'}"
                    echo "Target Branch: ${env.CHANGE_TARGET ?: 'Not a PR'}"
                    echo "Author: ${env.CHANGE_AUTHOR ?: 'Not a PR'}"
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
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
