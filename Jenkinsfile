#!groovy
stage('build') {
    echo 'build'
}
stage('test') {
    echo 'test' 
}
stage('deploy') {
    timeout(time:1, unit:'DAYS') {
        input message:'Approve deployment?', submitter: 'it-ops'
    }
    echo 'deploy'
}