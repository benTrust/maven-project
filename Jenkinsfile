pipeline {
    agent any
    stages{
		stage('DEBUG INFO'){
            steps {
                echo $JAVA_HOME
            }
        }
		stage('DEBUG INFO 2'){
            steps {
                echo '%JAVA_HOME%'
            }
        }
		stage('DEBUG INFO 3'){
            steps {
                which java
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