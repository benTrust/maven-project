pipeline {
    agent any
    stages{
		stage('DEBUG INFO'){
            steps {
                bat 'mvn -version'
            }
        }
		stage('DEBUG INFO 2'){
            steps {
                bat 'echo %JAVA_HOME%'
            }
        }
        stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}