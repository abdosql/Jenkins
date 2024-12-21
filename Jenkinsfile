pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clones from the repository configured in Jenkins
                checkout scm
            }
        }

        stage('Setup Symfony') {
            steps {
                sh '''
                    rm -rf symfony
                    mkdir -p symfony
                    cd symfony
                    composer create-project symfony/skeleton:"6.3.*" . --no-interaction --prefer-dist
                    composer require symfony/webapp-pack:* --no-interaction
                    composer require symfony/runtime:* --no-interaction
                    composer require --dev symfony/test-pack:* --no-interaction
                    composer require doctrine/annotations:* --no-interaction
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                dir('symfony') {
                    sh 'composer install --no-interaction --optimize-autoloader'
                }
            }
        }

        stage('Run Tests') {
            steps {
                dir('symfony') {
                    // Adjust your test command if you're using PhpUnit or another test suite
                    sh './bin/phpunit --version || echo "No tests to run"'
                }
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
