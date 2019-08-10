pipeline {
    agent any

    
    stages {
        
        stage('Information') {
            steps {
                echo "Running Buid num: ${env.BUILD_ID} on Jenkins ${env.JENKINS_URL}"
                echo "BUILD_NUMBER" :: $BUILD_NUMBER
                echo "BUILD_ID" :: $BUILD_ID
                echo "BUILD_DISPLAY_NAME" :: $BUILD_DISPLAY_NAME
                echo "JOB_NAME" :: $JOB_NAME
                echo "JOB_BASE_NAME" :: $JOB_BASE_NAME
                echo "BUILD_TAG" :: $BUILD_TAG
                echo "EXECUTOR_NUMBER" :: $EXECUTOR_NUMBER
                echo "NODE_NAME" :: $NODE_NAME
                echo "NODE_LABELS" :: $NODE_LABELS
                echo "WORKSPACE" :: $WORKSPACE
                echo "JENKINS_HOME" :: $JENKINS_HOME
                echo "JENKINS_URL" :: $JENKINS_URL
                echo "BUILD_URL" ::$BUILD_URL
                echo "JOB_URL" :: $JOB_URL               
                
                
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
