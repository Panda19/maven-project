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
    }
}
