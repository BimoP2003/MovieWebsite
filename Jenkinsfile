pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    echo "Cloning repository..."
                    git branch: 'main', url: 'https://github.com/BimoP2003/MovieWebsite.git'
                }
            }
        }

        stage('Create ZIP') {
            steps {
                script {
                    def timestamp = new Date().format("yyyy-MM-dd_HH-mm-ss")

                    def downloadsPath = "C:/Users/userpro/Downloads"  

                    def zipFileName = "${downloadsPath}/MovieWebsite_${timestamp}.zip"

                    echo "Creating ZIP file: ${zipFileName}"

                    bat """
                    powershell Compress-Archive -Path * -DestinationPath ${zipFileName}
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        always {
            echo 'Pipeline completed!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
