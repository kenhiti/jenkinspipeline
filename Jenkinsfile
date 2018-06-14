pipeline{
    agent any

    stages{
        stage('build'){
            step{
                sh 'mvn clean package'
            }

            post{
                success{
                    echo 'Archiving now'
                    archiveArtifacts artifact: '**/target/*.war'
                }
            }
        }
    }
}