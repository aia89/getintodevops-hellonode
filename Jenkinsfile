node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("aiados/getintodevops-hellonode")
    }

       //stage('Test image') {
        /* We test our image with a simple smoke test:
         /* Run a curl inside the newly-build Docker image */

        //app.inside {
            //sh 'curl http://localhost:8000 || exit 1'
        //}
    //}
    
    stage('Docker Login') {
                sh "docker login --username  $USERNAME  --password $PASSWORD " 
            }
            stage('Docker Push') {
                if (params.pushLatest) {
                    println('Pushing the image to latest version!!')
                    sh "docker tag artemis aiados/docker-jenkins:latest"
                    sh "docker push aiados/docker-jenkins:latest"

                    } 
            }
}

    //stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        //docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
           // app.push("${env.BUILD_NUMBER}")
            //app.push("latest")
        //}
    //}

