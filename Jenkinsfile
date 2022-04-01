pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-token')
	}

	stages {

        stage('install') {

			steps {
				sh 'npm install'
			}
		}

		stage('Build') {

			steps {
				sh 'sudo docker build -t ndrohith09/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'sudo docker push ndrohith09/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}