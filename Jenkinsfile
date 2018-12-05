properties([pipelineTriggers([githubPush()])])

node('linux') {   
    stage('Test') {    
        git'https://github.com/dwassswa/java-project.git'
        sh'ant -buildfile test.xml'  
    }   
    stage('Build') {    
        sh'ant'   
        
    }   
    stage('Results') {    
        junit'reports/*.xml'   
        
    }
    
}
