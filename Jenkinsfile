node ('ubuntu'){
    def app
    environment {
        DOCKERHUB_CREDENTIALS = credentials('tontonlaforce')
    }
    stage('Cloning Git') {
        /* Let's make sure we have the repository cloned to our workspace */
       checkout scm
    }

    stage('Build-and-Tag') {
        steps {
                sh 'sudo docker build -t tontonlaforce/snake .'
        }
    }


}
