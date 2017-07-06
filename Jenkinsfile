node("docker") {
    docker.withRegistry("https://github.com/kblack789/jenkinsdockerdemo.git", "dockergit-registry") {
    
        git url: "https://github.com/kblack789/jenkinsdockerdemo.git", credentialsId: '<<your-git-credentials-id>>'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
