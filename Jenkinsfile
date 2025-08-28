pipeline {
    agent any
    stages {
        stage('Build') {
            when {
                branch 'development'
            }
            steps {
                echo "Running build step on development branch..."
                // Example build command
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                echo "Running tests for all branches..."
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def buildNumber = input(
                        id: 'userInput', 
                        message: 'Enter current build number:',
                        parameters: [string(defaultValue: "${env.BUILD_NUMBER}", description: 'Build Number')]
                    )
                    echo "Deploying build number ${buildNumber}"
                }
            }
        }
    }
