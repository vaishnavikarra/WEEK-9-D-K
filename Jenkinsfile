pipeline{
    agent any
    stages{
        stage ("Build Docker Image"){
            steps{
                echo "Build Docker Image"
                bat "docker build -t kubedemoapp:v1 ."
            }
        }
        stage ("Docker Login"){
            steps{
                bat "docker login -u vaishnavikarra -p Harekrishna8*"
            }
        }
        stage("push Docker Iamge to Docker Hub"){
            steps {
                echo "push Docker Image to docker hub"
                bat "docker tag kubedemoapp:v1 vaishnavikarra/week9kubenetes:t1"
                bat "docker push vaishnavikarra/week9kubenetes"


            }
        }
        stage("Deploy to Kubernetes"){
            steps{
                bat "kubectl apply -f deployment.yaml --validate=false"
                bat "kubectl apply -f service.yaml"
            }
        }
    }
    post{
        success{
            echo 'Pipeline completed scucessfull!'

        }
        failure{
            echo "Pipeline failed.Please check the logs."
        }
    }
}