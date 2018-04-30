pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'php --version'
            }
        }
        stage('Tests') {
            parallel {
                stage('Test On Chrome') {
                    agent {
                        docker { image 'php' }
                    }
                    steps {
                        echo "Test for Firefox"
                    }
                }
                stage('Test On Firefox') {
                    agent {
                        docker { image 'php' }
                    }
                    steps {
                        echo "Tests for Firefox"
                    }
                }
            }
        }
        stage('Deploy'){
            steps {
                sh 'php --version'
            }
        }
    }
}
