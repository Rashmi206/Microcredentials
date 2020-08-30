pipeline {
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
	    stage('Run Discovery Service') {
            steps {
                echo 'Running Discovery Service...'
				bat 'cd ./discovery-service/ && mvn spring-boot:run'
            }
        }
        stage('Run API Gateway') {
            steps {
                echo 'Running API Gateway...'
				bat 'cd ./api-gateway/ && mvn spring-boot:run'
            }
        }
		stage('Run Car Service') {
            steps {
                echo 'Running Car Service...'
				bat 'cd ./car-service/ && mvn spring-boot:run'
            }
        }
    }
}
