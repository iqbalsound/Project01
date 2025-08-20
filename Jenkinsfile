pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/iqbalsound/Project01.git'
            }
        }

        /*stage('Build') {
            steps {
                echo 'Building project...'
                // If it’s just static files for Nginx, no build is required.
                // For Node/Java etc., run build commands here.
            }
        }*/

        /*stage('Test') {
            steps {
                echo 'Running tests...'
                // Add test commands here (npm test, mvn test, pytest, etc.)
            }
        }*/
	
/*		stage ('syncing Git Repo') {
		  steps {
			sh 'rsync -a /home/iqbal/Project01  iqbal@100.0.0.10:/usr/share/nginx/html'
	}
	}
*/
        stage('Deploy to Nginx') {
            steps {
                sshPublisher(publishers: [
                    sshPublisherDesc(
                        configName: 'nginx-server',
                        transfers: [
                            sshTransfer(
                                sourceFiles: '/home/iqbal/Project01/',
                                removePrefix: '',
                                remoteDirectory: '/usr/share/nginx/html',
                                execCommand: 'rsync -a /home/iqbal/Project01/  iqbal@100.0.0.10:/usr/share/nginx/html/'
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
// /usr/share/nginx/html
