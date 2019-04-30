pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                if(isUnix()){
                    sh 'mvn clean package'
                }else{
                    bat 'mvn clean package'
                }
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to Staging'){
            steps {
                build job: 'deploy-to-staging'
            }
        }
    }
}
