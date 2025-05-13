pipeline {
    agent any
 
    tools {
        git 'git' // Use the Git tool configured in Jenkins
        maven 'maven-3.8.6' 
    }

    stages {
        stage('build') {
            steps {
                echo 'Building...'
                bat 'mvn clean package'
            }
        }
        stage('capture') {
            steps {
                echo 'Capturing results...'
                archiveArtifacts '**/target/*.jar'
                junit '**/target/surefire-reports/TEST*.xml'
                jacoco()
            }
        }
    }
}
