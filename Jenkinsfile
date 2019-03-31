pipeline {
    agent any

    triggers {
         pollSCM('* * * * *')
     }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        sh "mvn --version"
                    }
                }

                stage ("Deploy to Production"){
                    steps {
                        sh "mvn -h"
                    }
                }
            }
        }
    }
}
