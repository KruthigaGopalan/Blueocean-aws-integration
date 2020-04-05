pipeline {
    agent any
    stages {
        stage ('Lint HTML') {
            steps {
                sh 'tidy -q -e artifacts/*.html'
            }
        }
        stage ('Upload to AWS'){
            steps {
                withAWS(region: 'us-east-1', credentials: 'blueocean') {
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'artifacts/index.html', bucket: 'c3pipelines-devops')
                }
            }
        }
    }
}
