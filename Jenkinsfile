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
  }
}

