pipeline {
    agent any

    stages {

        stage('Identify Branch') {
            steps {
                echo "Branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Auto Build - Develop') {
            when {
                branch 'develop'
            }
            steps {
                echo "✅ Auto build for develop branch"
                sh 'echo Building develop code'
            }
        }

        stage('Approval for Main') {
            when {
                branch 'main'
            }
            steps {
                input message: 'Approve deployment to MAIN?', ok: 'Approve'
            }
        }

        stage('Build Main') {
            when {
                branch 'main'
            }
            steps {
                echo "🚀 Building main branch after approval"
                sh 'echo Building main code'
            }
        }
    }
}
