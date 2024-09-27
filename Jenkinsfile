pipeline {
    agent any

    // triggers {
    //     cron('*/5 * * * *')  // Schedule to run every 5 minutes
    // }

    stages {
        stage('Backup') {
            steps {
                script {
                    // Run the backup script from the /opt/ directory
                    sh '/opt/backup.sh'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    // Command to remove temporary jobs or files (e.g., jobs ending with @tmp)
                    sh "rm -rf /opt/backup/backup_${DATE}/*@tmp"
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
