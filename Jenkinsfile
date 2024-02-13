node('App-Server-CWEB2140')
{
    def app
    stage('Clone Git')
    {
        // Clone the repository
        checkout scm
    }
    stage('Build and tag')
    {
        app = docker.build("noahbartell/carweb1")
    }
    stage('Post to Docker Hub')
    {
        docker.withRegistry('https://registry.hub.docker.com', 'dckr_pat_Y-lZ7z1Xs7EGGeNYcXa6RBIZ9hY')
        {
            app.push("latest")
        }
    }
    stage('Pull and Deploy')
    {
        sh 'docker-compose down'
        sh 'docker-compose up -d'
    }
}