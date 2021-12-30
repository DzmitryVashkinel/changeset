scm {
    git {
        remote {
            name('origin') 
            url('https://github.com/DzmitryVashkinel/changeset.git')
        }
        branch('${sha1}')
    }
}
pipeline {
    agent any
    stages {
        stage('Change file'){
            when { changeset "repo/*" }
            steps {
                sh '''
                echo "Files in repo changed"
                '''
            }
        }
        stage('File not change'){
            steps {
                sh '''
                echo "Files in repo NOT changed"
                echo "Hello"
                '''
            }
        }
    }
}
