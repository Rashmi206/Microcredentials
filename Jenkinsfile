pipeline {
	environment { 
		registry = "rk20" 
		registryCredential = 'docker-credentials'
	}	

    agent any

    stages {
        stage('Build Discovery Service') {
            steps {
                echo 'Building Discovery Service...'
				bat 'cd ./discovery-service/ && mvn clean install'
            }
        }
        stage('Build API Gateway') {
            steps {
                echo 'Building API Gateway...'
				bat 'cd ./api-gateway/ && mvn clean install'
            }
        }
		stage('Build Car Service') {
            steps {
                echo 'Building Car Service...'
				bat 'cd ./car-service/ && mvn clean install'
            }
        }
        stage('Test Discovery Service') {
            steps {
                echo 'Testing Discovery Service...'
				bat 'cd ./discovery-service/ && mvn test'
            }
        }
        stage('Test API Gateway') {
            steps {
                echo 'Testing API Gateway...'
				bat 'cd ./api-gateway/ && mvn test'
            }
        }
		stage('Test Car Service') {
            steps {
                echo 'Testing Car Service...'
				bat 'cd ./car-service/ && mvn test'
            }
        }
		stage('Push Image to Dockerhub'){
			steps{
				bat 'docker-compose build && docker-compose push'
			}
		}
		
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
				bat 'docker-compose up --build -d'
            }
        }
    }
}
