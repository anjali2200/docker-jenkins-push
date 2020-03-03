  
node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("anjalik2019/kgl2020")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
        docker.withRegistry('https://registry.hub.docker.com', 'anjalik2019') {
            app.push("${env.BUILD_NUMBER}")
            app.push("pipelinetag")
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }
}
