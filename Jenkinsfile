pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/iqbalsound/Project01.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                // If it’s just static files for Nginx, no build is required.
                // For Node/Java etc., run build commands here.
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add test commands here (npm test, mvn test, pytest, etc.)
            }
        }

        stage('Deploy to Nginx') {
            steps {
                sshPublisher(publishers: [
                    sshPublisherDesc(
                        configName: 'nginx-server',
                        transfers: [
                            sshTransfer(
                                sourceFiles: '**/*',
                                removePrefix: '',
                                remoteDirectory: '/usr/share/nginx/html', //'/home/iqbal/webserver/html/',
                                execCommand: 'sudo systemctl restart nginx'
                            )
                        ],
                        usePromotionTimestamp: false,
                        verbose: true
                    )
                ])
            }
        }
    }
}
