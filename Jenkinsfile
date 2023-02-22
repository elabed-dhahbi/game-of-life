pipeline {
    agent {
        label 'jdk11'
    }

    parameters {
        choice(name: 'GOAL', choices: ['dev', 'test', 'prod'], description: 'Select the environment to deploy to.')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'sprint1_develop', url: 'https://github.com/elabed-dhahbi/game-of-life.git'
            }
        }

        stage('Build the Code and SonarQube Analysis') {
            steps {
                sh 'mvn clean package sonar:sonar'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
                archive 'target/surefire-reports'
            }
        }

        stage('Deploy') {
            steps {
                sh "echo Deploying to ${params.GOAL}"
            }
        }
    }

    post {
        failure {
            mail to: 'abeddahbi2s@gmail.com', subject: 'Build failed', body: "The build of ${env.JOB_NAME} on ${env.NODE_NAME} has failed. Please check the console output: ${env.BUILD_URL}"
        }
    }
}
