pipeline {
    agent any

    environment {
        // Define any environment variables here
        // Example: JAVA_HOME = '/path/to/java'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code...'
                git 'https://github.com/AnjanaK93/ServiceRegistry.git', branch:'main'
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

        stage('Package') {
            steps {
                echo 'Packaging the application...'
                bat 'mvn package' // Use 'sh' for Linux
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                bat 'copy target/eureka-server.jar C:\Users\Administrator\Documents\ProjectMicroserver\Deployment'

                // Add your deployment steps here, e.g., copying the jar to a server
                // Example: bat 'copy target/eureka-server.jar C:\\path\\to\\deploy'
            }
        }
    }


}
