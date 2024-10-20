pipeline {
    // Define the agent
    agent any

    // Define the tools required
    tools {
        // "mymaven" should be configured under Global Tool Configuration in Jenkins
        maven 'mymaven'
    }

    stages {
        stage('Clone repo') {
            steps {
                // Clone the repository
                git 'https://github.com/github-simplilearn-net/MavenBuild.git'
            }
        }

        stage('Compile Code') {
            steps {
                // Run Maven compile
                sh 'mvn compile'
            }
        }

        stage('Test Code') {
            steps {
                // Run Maven tests
                sh 'mvn test'
            }

            post {
                success {
                    // Publish JUnit test results
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package Code') {
            steps {
                // Package the code
                sh 'mvn package'
            }
        }
    }
}
