pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Piyushjangid01/loginapp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image"
                sh 'docker build -t loginapp-ds .'
            }
        }

        stage('Docker Login and Push') {
            steps {
                echo "Logging into DockerHub and pushing image"
                sh 'docker login -u piyushj01 -p Piyush@0001'
                sh 'docker tag loginapp-ds piyushj01/loginapp-ds:latest'
                sh 'docker push piyushj01/loginapp-ds:latest'
            }
        }
         
    } 

}