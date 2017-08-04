pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Adding GitHub remote...'
                sh 'if git remote show | grep "github"; then echo 'Already added'; else git remote add github git@github.com:chustedde/octo-jenkins.git; fi'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sshagent(['octojenkins2']) {
                    sh 'git fetch'
                    sh 'git checkout master'
                    sh 'git pull'
                }
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