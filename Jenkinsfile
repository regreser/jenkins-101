#!groovy
def checkSkipStage = true;

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

def skipStage(stageName) {
    stageName == null ? 'build' : stageName;
    echo stageName;
    sh 'env'
    if (env.CHECK_POINT == stageName) {
        checkSkipStage = false;
        return;
    }
    currentBuild.result = 'ABORTED';
    try {
        timeout(time: 1, unit: 'NANOSECONDS');
    } catch (timeout) {

    }
}