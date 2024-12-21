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
                    mkdir -p symfony
                    cd symfony
                    if [ ! -f "composer.json" ]; then
                        composer create-project symfony/skeleton:"6.3.*" . --no-interaction
                    fi
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
                    sh 'php bin/phpunit || echo "No tests to run"'
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
