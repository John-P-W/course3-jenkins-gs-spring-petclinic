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
        stage('Parallel Tests') {
          parallel {
            stage('testsA') {
                steps {
                  echo "test set A"
                  sleep 2
                  sleep 4
                }
            }
            stage("testsB") {
              steps {    
                echo "test set B"
                sleep 3
              }
            }
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
