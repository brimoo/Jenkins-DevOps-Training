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
                timeout(time: 1, unit: 'MINUTES') {
                    sh './health-check.sh'
                }
            }
        }
    }
    post {
        always {
            echo 'Testing has finished'
        }
        success {
            echo 'Build was a success! Woohoo!'
        }
        failure {
            echo 'Build failed! Oh no!'
        }
    }
}