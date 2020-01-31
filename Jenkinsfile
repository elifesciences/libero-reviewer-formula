elifePipeline {
    def commit
    stage 'Checkout', {
        checkout scm
        commit = elifeGitRevision()
    }

    stage "Deploy to staging", {
        sh "./formula upgrade staging"
    }
}
