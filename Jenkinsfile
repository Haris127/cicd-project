pipeline {
    agent any
    environment {
        SONAR_HOME=tool 'Sonar'
    }
    stages {
        stage('Code From GitHub'){
            steps{
                git branch: 'main', credentialsId: 'github-credentials', url: 'https://github.com/Haris127/cicd-project.git'
            }
        }
        stage("Sonarqube Analysis"){
            steps{
                withSonarQubeEnv('Sonar') {
                    sh ''' $SONAR_HOME/bin/sonar-scanner -Dsonar.projectName=react-app \
                    -Dsonar.projectKey=react-app '''
                }
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build . -t hsris/react-app'
                }
            }
        }
        stage('Push image to Docker Hub'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                    sh 'docker login -u hsris -p ${dockerhubpwd}'    
                }
                sh 'docker push hsris/react-app'
                }
            }
        }
        stage('Deploy to k8s'){
            steps{
                script{
                    kubernetesDeploy (configs: 'deploymentservice.yaml', kubeconfigId: 'k8sconfigpwd')
                }
            }
        }
    }
}
