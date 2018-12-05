properties([pipelineTriggers([githubPush()])])
node('linux') {
  withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '6efc6f09-defe-47bc-a6ce-a7901202f4c2', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    stage('Test') {   
      sh 'ant'
      sh 'ant -f test.xml -v'
      junit 'reports/result.xml'   
    }
    stage('Build') {    
    sh 'ant' 
    sh 'ant -f build.xml -v'
    }
    stage('Report') {    
      sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
    
    } 
  }
}
