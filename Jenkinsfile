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
	 stage('quality') { 
            steps {
                sh 'mvn sonar:sonar' 
            }
        }
        }						   

    post {
        
        success {
            sh ''' git branch
           git checkout master
           git pull 
          git merge origin/feature'''
    
           withCredentials([usernamePassword(credentialsId: 'gitpush', passwordVariable: 'pass', usernameVariable: 'name')]) {
            sh 'git push https://${name}:${pass}@github.com/padmarajugadam/gitpublish.git'
           }
        }
	 failure {
            echo 'I failed :('
        }
    }
}
