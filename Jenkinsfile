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
    echo env.CHECK_POINT;
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