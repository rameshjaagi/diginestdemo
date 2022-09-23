pipeline { 
    agent any 
   
    stages {
        stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('Sonarqube') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.8.6') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
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
