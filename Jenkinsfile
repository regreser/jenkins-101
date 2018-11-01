#!groovy
def checkSkipStage = true;

stage('build') {
    node {
        if (checkSkipStage) {
            if (!skipStage('build')) {
                doBuild();
            } else {
                markStageAsAbort();
            }
        } else {
            markStageAsAbort();
        }
    }
}
stage('test') {
    node {
        if (checkSkipStage) {
            if (!skipStage('test')) {
                doTest();
            } else {
                markStageAsAbort();
            }
        } else {
            markStageAsAbort();
        }
    }
}
stage('deploy') {
    node {
        if (checkSkipStage）{
            if (!skipStage('deploy')) {
                doDeploy();
            } else {
                markStageAsAbort();
            }
        } else {
            markStageAsAbort();
        }
    }
}

def skipStage(stageName) {
    if (env.CHECK_POINT == null && env.CHECK_POINT == stageName) {
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
    timeout(time:1, unit:'NANOSECONDS') {
        
    }
}
