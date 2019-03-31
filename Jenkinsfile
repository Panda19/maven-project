pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                echo "Its Building the Code"
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }    
        stage ('Deployments'){
            parrallel{
                stage ('Deploy to Staging') {
                    steps {
                     sh "mvn --version"
                    }
                }
            
                 stage ('deploytoprod'){
                    steps{
                      sh "mvn -h"
                    }
                 }
            }
        }
     }
}
