pipeline {
    agent {
        label 'jdk11'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'sprint1_develop',url: 'https://github.com/elabed-dhahbi/game-of-life.git'
            }
        }
        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Run JUnit Tests') {
            steps {
                junit '**/surefire-reports/*.xml'
		archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
    }
}

