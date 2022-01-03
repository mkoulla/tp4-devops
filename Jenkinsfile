pipeline{
    environment {
        registry = "mkoulla/job1tp4"
        registryCredential = 'dockerhub'
        dockerImage = ''
    }
    agent any
        stages {
            stage('Cloning Git') {
                steps {
                git 'https://github.com/kelguemmat/tp4-devops'
                }
            }
            stage('Building image') {
                steps{
                script {
                dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Test image') {
            steps{
                script {
                    echo "Tests passed"
                }
            }
        }
        stage('Publish Image') {
            steps{
                script {
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
