pipeline { 
    agent any 
   
    stages {
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('Sonarqube') {
                withMaven(maven:'Maven 3.5') {
                        sh 'mvn clean package sonar:sonar'
                }
                }
                }
                }
        stage('Build') { 
            steps { 
                buildName "# ${BUILD_NUMBER} Triggred on ${params.ENVIRONEMT}"
                buildDescription "this build is triggered on environment ${params.ENVIRONEMT}"
                echo "build stage"
                sh 'printenv'
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
