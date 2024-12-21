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
                    # Install Symfony CLI
                    curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | sudo -E bash
                    sudo apt install symfony-cli
                    
                    # Remove existing symfony directory and create new project
                    rm -rf symfony
                    mkdir symfony
                    cd symfony
                    symfony new . --no-git
                    
                    # Install additional packages
                    composer require webapp
                    composer require symfony/test-pack --dev
                    composer require doctrine/annotations
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    cd symfony
                    composer install
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    cd symfony
                    php bin/phpunit
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    cd symfony
                    symfony server:start -d
                '''
            }
        }
    }
}
