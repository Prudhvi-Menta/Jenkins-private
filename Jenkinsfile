pipeline {
    // This is pre-build section
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
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    // This is build
    stages {
        stage('Build') {
            steps {
                script{
                    sh """
                        echo "This is Build stage"
                        echo $Course
                        env
                        #sleep 12
                        echo "Hello ${params.PERSON}"
                        echo "Biography: ${params.BIOGRAPHY}"
                        echo "Toggle: ${params.TOGGLE}"
                        echo "Choice: ${params.CHOICE}"
                        echo "Password: ${params.PASSWORD}"
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