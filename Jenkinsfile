pipeline {
    agent any

    
    stages {
        
        stage('Information') {
            steps {
                echo "Running Buid number ${env.BUILD_ID} on Jenkins ${env.JENKINS_URL}"
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
