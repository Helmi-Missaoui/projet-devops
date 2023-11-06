imed gharbi
	
14:12 (il y a 8 minutes)
	
À moi
pipeline {
    agent any
    environment {
        
        DOCKERHUB_CREDENTIALS = credentials('docker_helmi')
    }
    stages {
        stage('Checkout'){
            agent any
            steps{
                
                git branch: 'main', url:'https://github.com/Helmi-Missaoui/projet-devops.git'
            }
        }
        stage('Init'){
            steps{
                
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Build'){
            steps {
                
                sh 'docker build -t imedgh/calculator-app:$BUILD_ID -f ./Dockerfile .'
                //sh 'docker build -t $DOCKERHUB_CREDENTIALS_USR/calculator-app:$BUILD_ID' 
            }
        }
        stage('Deliver'){
            steps {
                
                sh 'docker push imedgh/calculator-app:$BUILD_ID'
            }
        }
        stage('Cleanup'){
            steps {
            
            sh 'docker rmi imedgh/calculator-app:$BUILD_ID'
            sh 'docker logout'
            }
        }
    }
}