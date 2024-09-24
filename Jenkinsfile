pipeline {
    agent any

    triggers {
        cron('0 12 * * *')  // Schedule to run every 5 minutes
    }

    stages {
        stage('Backup') {
            steps {
                script {
                    // Run the backup script from the /opt/ directory
                    sh '/opt/backup.sh'
                }
            }
        }
    }

    post {
        success {
            echo 'Backup completed successfully!'
        }
        failure {
            echo 'Backup failed.'
        }
    }
}
