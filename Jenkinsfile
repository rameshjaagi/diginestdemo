pipeline { 
    agent any 
    buildName '${env.BUILD_NUMBER} Triggred on ${params.ENVIRONEMT}'
    buildDescription 'this build is triggered on environment ${params.ENVIRONEMT}'
    
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
                sleep 5
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy stage"
            }
        }
    }
}
