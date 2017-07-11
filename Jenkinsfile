pipeline{
    def mvnHome = tool 'M3'
    agent { label 'EPBYMINW1969' }
    stages {
        stage('Stack creation'){
           steps {
                jobDsl targets: "jobs.groovy"
            }
        }
        stage('Build and upload') {
            steps {
                build job: 'MNT-CD-module9-build-job',
                parameters: [string(name: 'ARTIFACT_NAME', value: 'helloworld-$BUILD_NUMBER')]
            }
        }
        stage('Get list and Deploy') {
            steps {
                build job: 'MNT-CD-module9-deploy-job',
                parameters: [string(name: 'ARTIFACT_NAME', value: 'helloworld-100.tar.gz')]
            }
        }
    }
}