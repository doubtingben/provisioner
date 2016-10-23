node("docker") {
    docker.withRegistry('https://hub.docker.com', 'doubtingben-dockerhub') {
    
        git url: "https://github.com/doubtingben/provisioner.git", credentialsId: 'doubtingben-github'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "doubtingben/provionser"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
