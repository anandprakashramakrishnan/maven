pipeline {
    agent any  // This defines the agent, which can be any available agent or node in your Jenkins setup

    environment {
        // You can define environment variables here (e.g., Java home, Maven settings)
        MAVEN_HOME = '/usr/local/maven'  // Update the path according to your system
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from Git
                git 'https://github.com/your-username/jenkins-demo.git'
            }
        }

        stage('Build') {
            steps {
                // Run Maven to build the project
                script {
                    // Maven build command
                    sh "'${MAVEN_HOME}/bin/mvn' clean install"
                }
            }
        }

        stage('Test') {
            steps {
                // Run tests (optional)
                script {
                    // Maven test command
                    sh "'${MAVEN_HOME}/bin/mvn' test"
                }
            }
        }

        stage('Deploy') {
            steps {
                // If you want to deploy the build, you can add deployment steps here
                // For now, just archive the artifact as an example
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            // Clean up or notify on completion (this section always runs after the pipeline)
            echo 'Pipeline completed.'
        }
        success {
            // Notify on success (e.g., send a success notification)
            echo 'Build was successful!'
        }
        failure {
            // Notify on failure (e.g., send a failure notification)
            echo 'Build failed!'
        }
    }
}

