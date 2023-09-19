pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Deploy') {
            steps {
                script {
                    // Replace with your remote server SSH details
                    def remoteServer = 'your_remote_server_ip'
                    def remoteUser = 'your_ssh_username'
                    def remoteDir = '/path/to/remote/deployment/directory'

                    sshagent(['your-ssh-credentials-id']) {
                        // Copy the Docker Compose files to the remote server
                        sh "scp docker-compose.yml ${remoteUser}@${remoteServer}:${remoteDir}/docker-compose.yml"

                        // SSH into the remote server and deploy the containers
                        sh "ssh ${remoteUser}@${remoteServer} 'cd ${remoteDir} && docker-compose down && docker-compose up -d'"
                    }
                }
            }
        }
    }
}
