pipeline {
    agent any
    tools {
        maven 'maven3.6.1' 
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                sh 'echo test'
            }
            post {
                always {
                    sh 'echo post'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh 'echo deliver'
            }
        }
    }
}
