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
        stage ('Deploy to staging'){
            steps {
                build job: 'deploytostaging'
            }
        }
        
        stage ('deploytoprod'){
            steps{
                timeout(time:5, unit:'DAYS'){
                  input message: 'Approve Prod Release?'
                }
                
                build job: 'deploytoprod'
            }
            post {
                success {
                    echo 'code dpely to prod'
                }
                
                failure {
                    echo 'deloyment failed'
                }
            }
        }
    }
}
