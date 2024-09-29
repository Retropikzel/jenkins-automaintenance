pipeline {
    agent built_in_node

    triggers {
        cron("59 23 * * 1") // Clean up every monday
    }

    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
    }

    stages {
        stage('Clean docker images') {
            steps {
                sh 'docker system prune -a -f'
                sh 'docker network prune -f'
            }
        }
    }

}

