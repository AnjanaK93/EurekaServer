pipeline {
    agent any

     tools {
            // Tools
            maven 'maven'
            jdk 'jdk-17'
        }


    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code...'
                git url: 'https://github.com/AnjanaK93/EurekaServer.git', branch:'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                bat 'mvn clean install -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'mvn test'
            }
        }



        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                bat 'docker build -t eureka-image .'
                bat 'docker run -p 8761:8761 -d --name registry-sr --network eureka-network eureka-image'

                // Add your deployment steps here, e.g., copying the jar to a server
                // Example: bat 'copy target/eureka-server.jar C:\\path\\to\\deploy'
            }
        }
    }


}
