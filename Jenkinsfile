pipeline{
    agent any
    tools{
        maven 'maven_3.9.1'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'tambyog', url: 'https://github.com/tambyog/devops-automation.git']])
                sh 'mvn clean install'
            }
        }
        stage('Build Docker Image'){
            steps{
                script{
                    sh 'docker build -t tambyog/devops-integration .'
                }
            }
        }
        stage('Push image to docker hub'){
            steps{
                script{
                    sh 'docker login -u tambyog -p Vitthala@11'
                    sh 'docker push tambyog/devops-integration'
                }
            }
        }
    }
}
