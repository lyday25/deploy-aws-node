pipeline {
  agent any
  
   tools {nodejs "node"}
    
  stages {
    stage("GitHub git cloning") {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'GITHUB_CREDENTIAL', url: 'https://github.com/lyday25/deploy-aws-node.git']])
                    //git branch: 'main', url: 'https://github.com/lyday25/deploy-aws-node.git' 
                }
            }
        }
     
    stage('starting npm installation.......') {
      steps {
        sh 'npm install'
      }
    }
  
     stage('Build Docker Image for the app') {
            steps {
                script {
                 
                  sh 'printenv'
                  sh 'git version'
                  //sh 'docker build -t lyday25/node-app:""$Build_ID"".'
                  sh 'docker build -t lyday25/node-app5.0 .'
                }
            }
        }


        stage('Docker Image deployment to DockerHub') {
            steps {
                script {
                  
                 withCredentials([string(credentialsId: 'DOCKERID', variable: 'DOCKERID')]) {
                    sh 'docker login -u lyday25 -p ${DOCKERID}'
            }
            //normally
            //sh 'docker push lyday25/node-app:""$Build_ID""'
            sh 'docker push lyday25/node-app5.0:latest'
        }
            }   
        }
         
     

  }
}
