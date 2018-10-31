#!groovy
def checkSkipStage = true;

node {
    sh 'env'
    stage('build') {
        when { skipStage('build') };
        echo 'build';
    }
    stage('test') {
        when { skipStage('test') };
        echo 'test';
    }
    stage('deploy') {
        when { skipStage('deploy') };
        input message:'Approve deployment?';
        echo 'deploy';
    }
}

def skipStage(stageName) {
    stageName = stageName == null ? 'build' : stageName;
    if (env.CHECK_POINT == stageName) {
        checkSkipStage = false;
        return false;
    }
    return true;
}