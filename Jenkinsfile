pipeline {
    agent { docker { image 'python:3.5.1' } }

    environment {
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }
 
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
        stage('Credentials') {
            steps {
                echo 'Using the cred plugin'
                echo 'echo aws-secret-access-key=$AWS_SECRET_ACCESS_KEY'
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
        unstable {
            echo 'Run was unstable!'
        }
        changed {
            echo 'State of the pipeline has changed!'
        }
    }
}