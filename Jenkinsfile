pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-portfolio'
        CONTAINER_NAME = 'my-portfolio1'
    }

    stages {
        stage('Git Clone') {
            steps {
                echo 'Cloning the repository...'
                checkout scm 
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t my-portfolio .'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub-credentials',
                        usernameVariable: 'DOCKER_USERNAME',
                        passwordVariable: 'DOCKER_PASSWORD'
                    )
                ]) {
                    sh '''
                        echo "$DOCKER_PASSWORD" |
                        docker login -u "$DOCKER_USERNAME" --password-stdin
                    '''
                }
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub-credentials',
                        usernameVariable: 'DOCKER_USERNAME',
                        passwordVariable: 'DOCKER_PASSWORD'
                    )
                ]) {
                    sh '''
                        docker tag my-portfolio "$DOCKER_USERNAME/my-portfolio:latest"
                        docker push "$DOCKER_USERNAME/my-portfolio:latest"
                    '''
                }
            }
        }

        stage('Docker Run') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub-credentials',
                        usernameVariable: 'DOCKER_USERNAME',
                        passwordVariable: 'DOCKER_PASSWORD'
                    )
                ]) {
                    sh '''
                        docker rm -f my-portfolio1 2>/dev/null || true

                        docker run -d \
                            --name my-portfolio1 \
                            -p 8081:80 \
                            "$DOCKER_USERNAME/my-portfolio:latest"
                    '''
                }
            }
        }

        stage('Docker Logout') {
            steps {
                sh 'docker logout || true'
            }
        }
    }
}
