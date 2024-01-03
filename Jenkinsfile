pipeline {
  agent any 
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello World"'
        sh '''
                  echo "Multiline shell steps works too"
                  ls -lah
          '''
      }
    }
    stage('Lint HTML') {
      steps {
          sh 'pwd'
          sh 'ls'
          sh 'tidy -q -e *.html'
      }
    }
    stage('Upload to s3') {
      steps{
        withAWS(credentials: 'aws', region: 'us-east-1') {
          s3Upload (pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-project-jenkins')
        }
      }
    }
  }
}