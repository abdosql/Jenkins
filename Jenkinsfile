pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clones from the repository configured in Jenkins
                checkout scm
            }
        }

        stage('Install Composer Dependencies') {
            steps {
                sh 'composer install --no-interaction --optimize-autoloader'
            }
        }

        stage('Run Tests') {
            steps {
                // Adjust your test command if you're using PhpUnit or another test suite
                sh 'php bin/phpunit'
            }
        }

        stage('Build Docker Images') {
            steps {
                // Build images as defined in your docker-compose file
                sh 'docker-compose build'
            }
        }

        stage('Deploy') {
            steps {
                // Run containers in detached mode
                sh 'docker-compose up -d'
            }
        }
    }
}
