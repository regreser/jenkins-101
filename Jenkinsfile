#!groovy
def checkSkipStage = true;
def checkPoint = env.CHECK_POINT;

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
    stageName == null ? 'build' : stageName;
    echo stageName;
    if (checkPoint == stageName) {
        checkSkipStage = false;
        return;
    }
    currentBuild.result = 'ABORTED';
    try {
        timeout(time: 1, unit: 'NANOSECONDS');
    } catch (timeout) {

    }
}