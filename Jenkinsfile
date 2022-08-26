pipeline { 
    agent any 
    
    triggers {
  cron 'H/05 * * * *'
}
    stages {
        stage('Build') { 
            steps { 
                echo "build stage"
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'Github-creds', url: 'https://github.com/rameshjaagi/diginestdemo.git']]])
            }
        }
        stage('Test'){
            steps {
                echo "Test stage"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy stage"
            }
        }
    }
}
