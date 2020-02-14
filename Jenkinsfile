elifePipeline {
    def commit
    stage 'Checkout', {
        checkout scm
        commit = elifeGitRevision()
    }

    stage 'Helm build', {
        sh "helm dependency build ./helm/libero-reviewer"
    }

    stage 'Deploy to staging', {
        sh "./formula upgrade staging"
    }
}
