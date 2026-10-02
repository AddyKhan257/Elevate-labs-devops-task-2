pipeline {
    agent any

    environment {
        IMAGE     = 'nodejs-demo-app'
        CONTAINER = 'nodejs-demo-app'
    }

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t $IMAGE:$BUILD_NUMBER -t $IMAGE:latest .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run --rm $IMAGE:$BUILD_NUMBER npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker rm -f $CONTAINER || true
                    docker run -d --name $CONTAINER -p 3000:3000 $IMAGE:$BUILD_NUMBER
                    sleep 3
                    docker exec $CONTAINER wget -qO- http://localhost:3000
                '''
            }
        }
    }

    post {
        success { echo 'Pipeline finished: app deployed on port 3000' }
        failure { echo 'Pipeline failed, check the stage logs' }
    }
}
