#!groovy
def checkSkipStage = true;

stage('build') {
    node {
        echo checkSkipStage;
        echo !skipStage('build');
        if (checkSkipStage == false || !skipStage('build')) {
            doBuild();
        } else {
            markStageAsAbort();
        }
    }
}
stage('test') {
    node {
        if (checkSkipStage == false || !skipStage('test')) {
            doTest();
        } else {
            markStageAsAbort();
        }
    }
}
stage('deploy') {
    node {
        if (checkSkipStage == false || !skipStage('deploy')) {
            doDeploy();
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
