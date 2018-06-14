pipeline{
    agent any

    stages{
        stage('build'){
            steps{
                sh 'mvn clean package'
            }

            post{
                success{
                    echo 'Archiving now'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}