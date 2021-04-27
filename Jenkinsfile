pipeline {
    agent any
    triggers { pollSCM('* * * * *')}
    stages {
        // implicit checkout stage
        stage('Build') {
            steps {
                sh './mvnw clean package'
                // sh 'true'
            }
        }
    }
    post {
        always {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
        }
        // // Whenever build status is different from previous build
            // changed {
            // emailext attachLog: true,
            // body: 'Please go to ${BUILD_URL} and verify the build',
            // compressLog: true,
            // to: "test@jenkins",
            // subject: "Job \'${JOB_NAME}\' (${BUILD_NUMBER}) ${currentBuild.result}"
        // }
    }
}