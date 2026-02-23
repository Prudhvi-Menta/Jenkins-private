pipeline {
    agent {
        node {
            label 'jenkins-agent'
        }
    }
    environment{
        Course="Jenkins"
    }
    stages {
        stage('Build') {
            steps {
                script{
                    sh """
                        echo "This is Build stage"
                        echo $Course
                        env
                    """
                }
            }
        }
        stage('Test') {
            steps {
                script{
                    sh """
                        echo "This is Test stage"
                        echo $Course
                    """
                }
            }
        }
        stage('Deploy') {
            steps {
                 script{
                    sh """
                        echo "This is Deploy stage"
                        echo $Course
                    """
                }
            }
        }
    }

    post{
        always{
            echo "I will execute in post section."
            cleanWs()
        }
        success{
            echo "I will execute if pipeline succeded."
        }
        failure{
            echo "I will execute if pipeline failed."
        }
    }
}