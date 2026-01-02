pipeline {
    agent any

    environment {
        FLYWAY_URL = 'jdbc:postgresql://localhost:5432/cars1'
        FLYWAY_USER = 'postgres'
        FLYWAY_PASSWORD = 'Xznm@9021'
        FLYWAY_LOCATIONS = 'filesystem:D:\flywaydemo\flywaydemo2'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mahendrarejeetha/flyway-cars-demo'
            }
        }

        stage('Flyway Migrate') {
            steps {
                sh '''
                flyway -url=$FLYWAY_URL \
                       -user=$FLYWAY_USER \
                       -password=$FLYWAY_PASSWORD \
                       -locations=$FLYWAY_LOCATIONS migrate
                '''
            }
        }
    }

    post {
        success {
            echo 'Database migration successful!'
        }
        failure {
            echo 'Migration failed, check logs!'
        }
    }
}