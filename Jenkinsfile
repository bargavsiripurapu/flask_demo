 pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker_hub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/bargavsiripurapu/flask_demo.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t devopshub123/flask_demo:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push devopshub123/flask_demo:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
