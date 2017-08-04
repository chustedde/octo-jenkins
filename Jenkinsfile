pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Adding GitHub remote...'
                sh 'git remote add github git@github.com:chustedde/octo-jenkins.git'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                echo '(No tests yet)'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Pushing to GitHub...'
                sshagent(['octojenkins2']) {
                    sh 'git push -u github master'
                }
            }
        }
    }
}