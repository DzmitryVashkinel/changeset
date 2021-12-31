job('example') {
    scm {
        git {
            remote {
                url("https://github.com/DzmitryVashkinel/changeset.git")
                refspec('+refs/pull/*:refs/remotes/origin/pr/*')
            }
            branch('master')
        }
    }
    triggers {
        githubPullRequest {
            admin('user_1')
            admins(['user_2', 'user_3'])
            userWhitelist('you@you.com')
            userWhitelist(['me@me.com', 'they@they.com'])
            orgWhitelist('my_github_org')
            orgWhitelist(['your_github_org', 'another_org'])
            cron('H/5 * * * *')
            triggerPhrase('OK to test')
            onlyTriggerPhrase()
            useGitHubHooks()
            permitAll()
            autoCloseFailedPullRequests()
            allowMembersOfWhitelistedOrgsAsAdmin()
            extensions {
                commitStatus {
                    context('deploy to staging site')
                    triggeredStatus('starting deployment to staging site...')
                    startedStatus('deploying to staging site...')
                    statusUrl('http://mystatussite.com/prs')
                    completedStatus('SUCCESS', 'All is well')
                    completedStatus('FAILURE', 'Something went wrong. Investigate!')
                    completedStatus('PENDING', 'still in progress...')
                    completedStatus('ERROR', 'Something went really wrong. Investigate!')
                }
            }
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
