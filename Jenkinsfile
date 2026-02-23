pipeline {
    agent {
        node {
            label 'jenkins-agent'
        }
    }
    environment{
        Course="Jenkins"
    }
    options{
        timeout(time: 10, unit: 'SECONDS')
        disableConcurrentBuilds()
    }
    stages {
        stage('Build') {
            steps {
                script{
                    sh """
                        echo "This is Build stage"
                        echo $Course
                        env
                        // sleep 12
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
        aborted{
            echo "This pipeline is aborted"
            echo "Job name is $JOB_BASE_NAME, Build id is $BUILD_NUMBER has failed against this git commit $GIT_COMMIT"
        }
    }
}