pipeline {
    agent { docker { image 'python:3.5.1' } }
 
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                retry(3) {
                    sh './script-not-found.sh'
                }
            }
        }
    }
}