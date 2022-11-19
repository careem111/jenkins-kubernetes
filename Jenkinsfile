 pipeline{
   agent {
     kubernetes {
       yaml '''
         apiVersion: v1
         kind: Pod
         spec:
           containers:
           - name: build-agent
             image: maven:alpine
	     ttyEnabled: true
             command: ['cat']
         '''
        }
    }
    stages {
      stage('Build') {
    	steps{
    	  container('build-agent')
	    sh 'mvn -version'
        	}
            }
        } 
    }
