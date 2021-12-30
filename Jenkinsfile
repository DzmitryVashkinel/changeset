scm {
    git {
        remote { 
            url('https://github.com/DzmitryVashkinel/changeset.git')
        }
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
