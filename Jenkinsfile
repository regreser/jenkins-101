#!groovy
def checkSkipStage = true

stage('build') {
    if (checkSkipStage) {
        skipStage('build')
    }
    echo 'build'
}
stage('test') {
    if (checkSkipStage) {
        skipStage('test')
    }
    echo 'test' 
}
stage('deploy') {
    if (checkSkipStage) {
        skipStage('deploy')
    }
    input message:'Approve deployment?'
    echo 'deploy'
}

def skipStage(stageName) {
    if (env.CHECK_POINT == stageName) {
        checkSkipStage = false;
        try {
            timeout(time: 15, unit: 'NANOSECONDS');
        } catch (timeout) {

        }
    }
}