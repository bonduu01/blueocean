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
                  sh 'tidy -q -e *.html'
              }
         }
         stage('Security Scan') {
              steps { 
                 //aquaMicroscanner imageName: 'alpine:latest', notCompliesCmd: 'exit 1', onDisallowed: 'fail'
                 aquaMicroscanner imageName: 'alpine:latest', notCompliesCmd: 'exit 4', onDisallowed: 'fail', outputFormat:'html'
              }
         }         
        //  stage('Upload to AWS') {
        //       steps {
        //           withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws_credential', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
        //           {
        //           sh 'echo "Uploading content with AWS creds"'
        //                s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'bonduu-static-jenkins-pipeline')
        //           }
        //       }
        //  }
     }
}
