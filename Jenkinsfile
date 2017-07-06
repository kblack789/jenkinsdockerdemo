node("docker") {
    docker.withRegistry("https://github.com/kblack789/jenkinsdockerdemo.git", "dockergit-registry") {
    
        git url: "https://github.com/kblack789/jenkinsdockerdemo.git", credentialsId: c94b2b30-87c4-4d60-9892-285c9406afaf
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "dockerpipelinedemo"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
