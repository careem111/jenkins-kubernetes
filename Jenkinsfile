 pipeline{
   agent {
     kubernetes {
       yaml '''
         apiVersion: v1
         kind: Pod
         spec:
           containers:
           - name: build-agent
             image: careem785/jenkins-build-agent:1.0
             ttyEnabled: true
             workingDir: /home/jenkins
             alwaysPullImage: false
             command: ['cat']
             serviceAccountName: jenkins-agent-ca
         '''
        }
    }
    stages {
      stage('Build') {
    	steps{
    	  container('build-agent')
	    sh 'date'
        	}
            }
        } 
    }
