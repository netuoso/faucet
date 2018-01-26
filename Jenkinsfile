node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
        app = docker.build("${env.BUILD_TAG}")
    }
    stage('Push image') {
        docker.withRegistry("${env.DOCKER_REGISTRY}", "${env.DOCKER_CREDENTIALS}") {
            app.push("${env.BUILD_TAG}")
        }
    }
}
