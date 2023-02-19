pipeline {
    agent {
        label 'jdk11'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'sprint1_develop', url: 'https://github.com/elabed-dhahbi/game-of-life.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
                archive 'target/surefire-reports'
            }
        }
    }

    post {
        failure {
            mail to: 'abeddahbi2s@gmail.com', subject: 'Build failed', body: "The build of ${env.JOB_NAME} on ${env.NODE_NAME} has failed. Please check the console output: ${env.BUILD_URL}"
        }
    }
}
