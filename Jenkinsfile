node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
       app = docker.build("test/devops")
    }

    stage('Push image') {
        docker.withRegistry('https://registry.local', 'nexus') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
