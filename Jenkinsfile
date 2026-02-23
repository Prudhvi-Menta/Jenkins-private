pipeline {
    agent {
        node {
            label 'jenkins-agent'
        }
    }
    stages {
        stage('Build') {
            steps {
                echo "This is Build stage"
            }
        }
        stage('Test') {
            steps {
                echo "This is Test stage"
            }
        }
        stage('Deploy') {
            steps {
                echo "This is Deploy stage"
            }
        }
    }

    post{
        always{
            echo "I will execute in post section."
            // cleanWs()
        }
        success{
            echo "I will execute if pipeline succeded."
        }
        failure{
            echo "I will execute if pipeline failed."
        }
    }
}