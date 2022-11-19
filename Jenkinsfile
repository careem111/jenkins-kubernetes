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
             tty: true
             command: ['cat']
             serviceAccountName: jenkins-admin
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
