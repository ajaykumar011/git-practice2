pipeline {
    // agent any
  
    options {
        timestamps()
    }
    
    environment {
    //Use Pipeline Utility Steps plugin to read information from pom.xml into env variables
    IMAGE = readMavenPom().getArtifactId()
    VERSION = readMavenPom().getVersion()
  }
    
    stages {
        
        stage('Environment') {
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
        
        stage('Build Version') {
            steps {
                echo 'Building..'
                sh 'mvn -v'
            }
		}
            
        stage('Build') {
              agent {
                 docker {
			/*
			* Reuse the workspace on the agent defined at top-level of Pipeline but run inside a container.
			* In this case we are running a container with maven so we don't have to install specific versions
			* of maven directly on the agent
			*/
          reuseNode true
          image 'maven:3.5.0-jdk-8'
                }
		
			steps {
			// using the Pipeline Maven plugin we can set maven configuration settings, publish test results, and annotate the Jenkins console
			withMaven(options: [findbugsPublisher(), junitPublisher(ignoreAttachments: false)]) {
			sh 'mvn clean findbugs:findbugs package'
			}
			}
		post {
			success {
			// we only worry about archiving the jar file if the build steps are successful
			archiveArtifacts(artifacts: '**/target/*.jar', allowEmptyArchive: true)
				}
			}
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
