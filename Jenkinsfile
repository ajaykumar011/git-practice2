pipeline {
  // agent any
  options {
        timestamps()
    }

  agent { docker { image 'maven:3.3.3' } }
   stages {
       stage('build') {
           steps {
               sh 'mvn --version'
               sh 'mvn clean install'
           }
       }

        stage('BuildInfo') {
            steps {
                echo "Running Buid num: ${env.BUILD_ID} on Jenkins ${env.JENKINS_URL}"
                echo "BUILD_NUMBER :: ${env.BUILD_NUMBER}"
                echo "BUILD_ID :: ${env.BUILD_ID}"
                echo "BUILD_DISPLAY_NAME :: ${env.BUILD_DISPLAY_NAME}"
                echo "JOB_NAME :: ${env.JOB_NAME}"
                echo "JOB_BASE_NAME :: ${env.JOB_BASE_NAME}"
                echo "BUILD_TAG :: ${env.BUILD_TAG}"
                echo "EXECUTOR_NUMBER :: ${env.EXECUTOR_NUMBER}"
                echo "NODE_NAME :: ${env.NODE_NAME}"
                echo "NODE_LABELS :: ${env.NODE_LABELS}"
                echo "WORKSPACE :: ${env.WORKSPACE}"
                echo "JENKINS_HOME :: ${env.JENKINS_HOME}"
                echo "JENKINS_URL :: ${env.JENKINS_URL}"
                echo "BUILD_URL ::${env.BUILD_URL}"
                echo "JOB_URL :: ${env.JOB_URL}"

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
