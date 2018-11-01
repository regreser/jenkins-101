#!groovy
def checkSkipStage = true;

currentBuild.displayName = '#' + env.BUILD_NUMBER

stage('build') {
    node {
        sh 'env'
        if (checkSkipStage && !skipStage('build')) {
            doBuild();
        } else {
            markStageAsAbort();
        }
    }
    env.CHECK_POINT = 'test';
}
stage('test') {
    node {
        if (checkSkipStage && !skipStage('test')) {
            doTest();
        } else {
            markStageAsAbort();
        }
    }
    env.CHECK_POINT = 'deploy';
}
stage('deploy') {
    input 'Do you approve deployment?'
    node {
        if (checkSkipStage && !skipStage('deploy')) {
            doDeploy();
        } else {
            markStageAsAbort();
        }
    }
}

def skipStage(stageName) {
    if (env.CHECK_POINT == "" || env.CHECK_POINT == stageName) {
        checkSkipStage = false;
        return false;
    }
    return true;
}

def doBuild() {
    echo 'build';
}

def doTest() {
    echo 'test';
}

def doDeploy() {
    echo 'deploy';
}

def markStageAsAbort() {
    try {
        timeout(time:1, unit:'NANOSECONDS') {}
    } catch(timeout) {

    }
    // currentBuild.result = 'ABORT'
}
