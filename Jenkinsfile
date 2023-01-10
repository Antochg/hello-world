pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                echo 'Testing..';
                echo 'Running npm run test..';
                npm run test;
            }
        }

        stage('Build') {
            steps {
                echo 'Building..'
                echo 'Running docker build . -t antochg/hello-world-app'
                docker build . -t antochg/hello-world-app
            }
        }

        stage('Push') {
            steps {
                echo 'Pushing..'
                echo 'Running docker push..'
                docker push antochg/hello-world-app
            }
        }
        
        stage('Deploy to preprod') {
            steps {
                echo 'Deploying to preprod..'
                set NODE_ENV=PREPROD
                docker run -it antochg/hello-world-app
            }
        }
        
        stage('Cleanup') {
            steps {
                echo 'Cleaning..'
                echo 'Running docker rmi..'
            }
        }

        stage('Deploy to prod') {
            steps {
                echo 'Deploying to prod..'
                set NODE_ENV=PREPROD
                docker run -it antochg/hello-world-app
            }
        }


        
    }
}