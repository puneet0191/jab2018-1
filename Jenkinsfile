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
                stage('Test On Windows') {
                    agent {
                        docker { image 'php' }
                    }
                    steps {
                        echo "Test for Firefox"
                        sh 'wget "https://chromedriver.storage.googleapis.com/2.35/chromedriver_linux64.zip"'
                        stash includes: 'chromedriver_linux64.zip', name: 'chromeD-Windows'
                    }
                }
                stage('Test On Linux') {
                    agent {
                        docker { image 'php' }
                    }
                    steps {
                        echo "Tests for Firefox"
                        sh 'wget "https://chromedriver.storage.googleapis.com/2.35/chromedriver_linux64.zip"'
                        stash includes: 'chromedriver_linux64.zip', name: 'chromeD-Linux'
                    }
                }
            }
        }
        stage('Deploy'){
            steps {
                unstash 'chromeD-Linux'
                unstash 'chromeD-Windows'
                sh 'php --version'
            }
        }
    }
}
