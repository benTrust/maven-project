pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: 'localhost', description: 'Staging Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
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

        stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        bat 'cp "C:/Program Files (x86)/Jenkins/jobs/mavenProjectPAC/lastSuccessful/archive/webapp/target/webapp.war" "C:/Program Files/Apache Software Foundation/apache-tomcat-9.0.14/webapps"'
                    }
                }
            }
        }
    }
}