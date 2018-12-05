properties([pipelineTriggers([githubPush()])])
node('linux') {   
  stage('Test') {   
    sh 'ant'
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'   
  }
  stage('Build') {    
    sh 'ant' 
    sh 'ant -f build.xml -v'
  }   
  
  
}
