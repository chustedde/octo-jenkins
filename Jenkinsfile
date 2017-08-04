pipeline {
    agent any

    stages {
        stage('Add remote') {
            steps {
                echo 'Adding GitHub remote...'
                sh 'if git remote show | grep "github"; then echo 'Already added'; else git remote add github git@github.com:chustedde/octo-jenkins.git; fi'
            }
        }
        stage('Pull changes') {
            steps {
                echo 'Testing...'
                sshagent(['octojenkins2']) {
                    sh 'git fetch'
                    sh 'git checkout master'
                    sh 'git pull'
                }
            }
        }
        stage('Push to GH') {
            steps {
                echo 'Pushing to GitHub...'
                sshagent(['octojenkins2']) {
                    sh 'git push -u github master'
                }
            }
        }
    }
}