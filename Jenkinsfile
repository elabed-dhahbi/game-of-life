pipeline {
     agent { label 'JDK8' }
     stages {
       stage ('SourceCode') {
          steps {
             git branh: 'sprint1_develop', url 'https://github.com/elabed-dhahbi/game-of-life.git'
          }
       }
       stage('Build the code') {
          steps {
             sh 'mvn clean package'
          }
       }
       stage('Archiving artifacts & Junit Test Results') {
           steps {
               junit stdioRetention: '', testResults: '**/surefire-reports/*.xml'
               archiveArtifacts artifacts: '**/*.war ,followSymlinks: false'
           }
       }
     
     }

}
