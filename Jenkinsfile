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
             command: ['cat']
             workingDir: /home/jenkins
             alwaysPullImage: false
             ttyEnabled: true
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
