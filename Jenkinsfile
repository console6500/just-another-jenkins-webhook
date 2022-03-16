pipeline {
    agent any

    // this section configures Jenkins options
    options {
        // only keep 10 logs for no more than 10 days
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))

        // cause the build to time out if it runs for more than 12 hours
        timeout(time: 12, unit: 'HOURS')

        // add timestamps to the log
        timestamps()
    }

    // this section configures triggers
    triggers {
          // create a cron trigger that will run the job every day at midnight
          // note that the time is based on the time zone used by the server
          // where Jenkins is running, not the user's time zone
          cron '@midnight'
    }

    // the pipeline section we all know and love: stages! :D
    stages {
        stage('Requirements') {
            steps {
                echo 'Installing requirements...'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Report') {
            steps {
                echo 'Reporting....'
                echo  "BRANCH_IS_PRIMARY           =  ${env.BRANCH_IS_PRIMARY}"
                echo  "BRANCH_NAME                 =  ${env.BRANCH_NAME}"
                echo  "CHANGE_AUTHOR               =  ${env.CHANGE_AUTHOR}"
                echo  "CHANGE_AUTHOR_DISPLAY_NAME  =  ${env.CHANGE_AUTHOR_DISPLAY_NAME}"
                echo  "CHANGE_AUTHOR_EMAIL         =  ${env.CHANGE_AUTHOR_EMAIL}"
                echo  "CHANGE_BRANCH               =  ${env.CHANGE_BRANCH}"
                echo  "CHANGE_FORK                 =  ${env.CHANGE_FORK}"
                echo  "CHANGE_ID                   =  ${env.CHANGE_ID}"
                echo  "CHANGE_TARGET               =  ${env.CHANGE_TARGET}"
                echo  "CHANGE_TITLE                =  ${env.CHANGE_TITLE}"
                echo  "CHANGE_URL                  =  ${env.CHANGE_URL}"
                echo  "TAG_DATE                    =  ${env.TAG_DATE}"
                echo  "TAG_NAME                    =  ${env.TAG_NAME}"
                echo  "TAG_TIMESTAMP               =  ${env.TAG_TIMESTAMP}"
                echo  "TAG_UNIXTIME                =  ${env.TAG_UNIXTIME}"
            }
        }
    }

    // the post section is a special collection of stages
    // that are run after all other stages have completed
    post {

        // the always stage will always be run
        always {

            // the always stage can contain build steps like other stages
            // a "steps{...}" section is not needed.
            echo "This step will run after all other steps have finished.  It will always run, even in the status of the build is not SUCCESS"
        }
    }
}
