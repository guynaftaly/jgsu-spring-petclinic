pipeline {
    agent any
    triggers { pollSCM('* * * * *') }

    stages {
        stage('Checkuot') {
            steps{
                git branch: 'main', url: 'https://github.com/guynaftaly/jgsu-spring-petclinic'
            }
        }
        
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
