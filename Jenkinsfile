pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('dockerhub')
    }
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
                sh 'ls *'
            }
        }
        stage('Build Image') {
            steps {
                //this will run dockerbuild with the jenkins build number
		sh 'docker build -t rangel9697/jenkinstest:$BUILD_NUMBER ./'
            }
        }
        stage('Docker Login') {
            steps {
                //this will login into docker without showing password
                sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'                
                }
            }
        stage('Docker Push') {
            steps {
                //this pushes the dockerbuild with our tag    
                sh 'docker push rangel9697/jenkinstest:$BUILD_NUMBER'
                }
            }
        }
    post {
		always {
			sh 'docker logout'
		}
	 }
    }