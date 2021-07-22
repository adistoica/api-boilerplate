pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git([url: 'https://github.com/adistoica/api-boilerplate.git', branch: 'main'])
            }
        }

        stage('Install tools') {
            steps {
               sh "npm install -g newman"
            }
        }

        stage('Execute') {
            steps {
               sh "newman run tests/smoke.postman_collection.json -e environments/dev.postman_environment.json -r cli,junit"
            }
        }
    }
}

