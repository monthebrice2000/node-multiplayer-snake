pipeline {
  agent {
    node {
      label 'app'
    }
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('tontonlaforce')
  }

  stages {

    stage('Cloning Git') {
      steps {
        checkout scm
      }
    }

    stage('Build-and-Tag') {
      steps {
        sh 'sudo docker build -t tontonlaforce/snake .'
      }
    }

    
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }

    stage('Push') {
      steps {
        sh 'sudo docker push tontonlaforce/snake:latest'
      }
    }

    stage('Pull-image-server') {
      steps {
        sh "sudo docker compose down"
        sh "sudo docker compose up -d"
      }
    }
  }
}

