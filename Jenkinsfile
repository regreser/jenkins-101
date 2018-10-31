#!groovy
def checkSkipStage = true;

node {
    sh 'env'
    stage('build') {
        if (checkSkipStage) {
            skipStage('build');
        }
        echo 'build';
    }
    stage('test') {
        if (checkSkipStage) {
            skipStage('test');
        }
        echo 'test';
    }
    stage('deploy') {
        if (checkSkipStage) {
            skipStage('deploy');
        }
        input message:'Approve deployment?';
        echo 'deploy';
    }
}

def skipStage(stageName) {
    stageName = stageName == null ? 'build' : stageName;
    if (env.CHECK_POINT == stageName) {
        checkSkipStage = false;
        return;
    }
    urrentBuild.result = 'ABORTED';
    timeout(time: 1, unit: 'NANOSECONDS');
}
