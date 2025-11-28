pipeline {
    agent any

    stages {
        stage('Pull Latest Code') {
            steps {
                echo 'Pulling latest code from GitHub...'
                bat """
                cd %WORKSPACE%
                git reset --hard
                git pull origin main
                """
            }
        }

        stage('Deploy to Local Folder') {
            steps {
                echo 'Copying files to local web folder...'
                bat """
                REM Change this path to your desired folder to serve the webpage
                set DEST=C:\\Users\\Kevin\\Documents\\WebPageTest
                if not exist "%DEST%" mkdir "%DEST%"
                xcopy /Y /E "%WORKSPACE%\\*" "%DEST%\\"
                """
            }
        }
    }

    post {
        success {
            echo 'Build and deploy finished successfully!'
        }
        failure {
            echo 'Something went wrong!'
        }
    }
}
