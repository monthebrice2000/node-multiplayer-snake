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
    /* This builds the actual image; synonymous to
         * docker build on the command line */
       /* app = docker.build("tontonlaforce/snake")*/
	steps {
        	sh 'sudo docker build -t tontonlaforce/snake .'
      	}
    }
    /*stage('Post-to-dockerhub') {

     docker.withRegistry('https://registry.hub.docker.com', 'tontonlaforce') {
            app.push("latest")
     }
    }*/

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

         sh "sudo docker compose down"
         sh "sudo docker compose up -d"
      }
}

