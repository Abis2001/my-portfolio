Pipeline{
    agent any
    sages{
        stage('git clone'){
            steps{
                echo 'Cloning the repository...' url 'https://github.com/Abis2001/my-portfolio.git'
            }
        }
        stage('docker build'){
            steps{
                sh 'docker build -t my-portfolio .'
            }
        }
        stage('docker login'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                }
            }
        }
        stage('docker run'){
            steps{
                sh 'docker run -d -p 80:80 --name=my-portfolio1 my-portfolio'
            }
        }
        stage('docker push'){
            steps{
                sh 'docker tag my-portfolio $DOCKER_USERNAME/my-portfolio:latest'
                sh 'docker push $DOCKER_USERNAME/my-portfolio:latest'
            }
        }
        stage('docker logout'){
            steps{
                sh 'docker logout'
            }
        }
    }
}