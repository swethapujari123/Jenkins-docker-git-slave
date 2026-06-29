pipeline {
    agent none

    stages {

        stage('Deploy Q1 to Slave1') {
            agent { label 'slave1' }

            steps {

                sh '''
                echo "===== USER ====="
                whoami

                echo "===== ID ====="
                id

                echo "===== WORKSPACE ====="
                pwd

                echo "===== DOCKER SOCKET ====="
                ls -l /var/run/docker.sock

                echo "===== DOCKER VERSION ====="
                docker --version

                echo "===== DOCKER PS ====="
                docker ps
                '''

                git branch: 'q1',
                    url: 'https://github.com/swethapujari123/Jenkins-docker-git-slave.git'

                sh '''
                docker cp index.html webserver:/usr/local/apache2/htdocs/index.html
                '''
            }
        }

        stage('Deploy Q2 to Slave2') {
            agent { label 'slave2' }

            steps {

                sh '''
                echo "===== USER ====="
                whoami
                id
                docker ps
                '''

                git branch: 'q2',
                    url: 'https://github.com/swethapujari123/Jenkins-docker-git-slave.git'

                sh '''
                docker cp index.html webserver:/usr/local/apache2/htdocs/index.html
                '''
            }
        }

        stage('Deploy Q3 to Slave3') {
            agent { label 'slave3' }

            steps {

                sh '''
                echo "===== USER ====="
                whoami
                id
                docker ps
                '''

                git branch: 'q3',
                    url: 'https://github.com/swethapujari123/Jenkins-docker-git-slave.git'

                sh '''
                docker cp index.html webserver:/usr/local/apache2/htdocs/index.html
                '''
            }
        }
    }
}
