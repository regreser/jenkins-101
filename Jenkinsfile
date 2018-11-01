#!groovy
def checkSkipStage = true;

stage('build') {
    node {
        if (checkSkipStage == false || !skipStage('build')) {
            doBuild();
        }
    }
}
stage('test') {
    node {
        if (checkSkipStage == false || !skipStage('test')) {
            doTest();
        }
    }
}
stage('deploy') {
    node {
        if (checkSkipStage == false || !skipStage('deploy')) {
            doDeploy();
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
