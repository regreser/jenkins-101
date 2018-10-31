#!groovy
def checkSkipStage = true;

node {
    sh 'env'
    stage('build') {
        if (checkSkipStage) {
            if (skipStage('build')) {
                currentBuild.result = 'ABORTED';
                try {
                    timeout(time: 1, unit: 'NANOSECONDS');
                } catch (timeout) {

                }
            }
        }
        echo 'build';
    }
    stage('test') {
        if (checkSkipStage) {
            if (skipStage('test')) {
                currentBuild.result = 'ABORTED';
                try {
                    timeout(time: 1, unit: 'NANOSECONDS');
                } catch (timeout) {

                }
            }
        }
        echo 'test';
    }
    stage('deploy') {
        if (checkSkipStage) {
            if (skipStage('deploy')) {
                currentBuild.result = 'ABORTED';
                try {
                    timeout(time: 1, unit: 'NANOSECONDS');
                } catch (timeout) {

                }
            }
        }
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