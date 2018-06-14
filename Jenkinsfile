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

        stage('Deploy to staging'){
            steps{
                build job: 'deploy-to-staging'
            }
        }

        stage('Deploy to production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message: 'Approve PRODUCTION Deployment?'
                }

                build job: 'deploy-to-prod'
            }

            post{
                success{
                    echo 'Code deployed to Production.'
                }

                failure{
                    echo 'Deployment in production failed'
                }
            }
        }
    }
}