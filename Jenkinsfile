pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Adding GitHub remote...'
                // sh 'git remote add github git@github.com:chustedde/octo-jenkins.git'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sshagent(['octojenkins2']) {
                    sh 'git fetch'
                    sh 'git checkout master'
                    sh 'git show-ref master'
                    sh 'git status'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Just getting info... Done!'
                //echo 'Pushing to GitHub...'
                //sshagent(['octojenkins2']) {
                //    sh 'git push -u github master'
                //}
            }
        }
    }
}