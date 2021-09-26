 pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
stage('Cloning our Git') { 

            steps { 

                git 'https://github.com/nagur/docker_pipeline.git' 

            }

        } 

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t nsudhakar/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push nsduhakar/nodeapp:latest'
			}
		}
	}
}
