pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    environment {
        HARBOR_URL = "harbor.7booster.cc"
        REPO_URL = "git@github.com:huangyisan/simple-nodejs-server.git"
        HELM_BRANCH = "release/helm"
    }
    stages {
         stage('Clone repository') { 
            steps {
                    sh '''
                    printenv
                    git branch -a
                    comm=$(git rev-list --tags --max-count=1)
                    echo \${comm}
                    lastTag=\$(git describe --tags `git rev-list --tags --max-count=1`)
                    echo \${lastTag}
                    git checkout ${lastTag}
                    '''
                    // script {
                    //     env.lastTag="${lastTag}"
                    // }
            }
        }

        stage('Build') { 
            steps { 
                sh 'docker build -f Dockerfile -t ${HARBOR_URL}/7booster/simple-nodejs-server:${lastTag} .'
                }
            }
        
        stage('Test'){
            steps {
                 echo 'Empty1'
            }
        }
    }
}
