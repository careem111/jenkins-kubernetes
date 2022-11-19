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
	           serviceAccountName: jenkins-agent-sa
	       '''
        }
    }
    stages {
      stage('Build') {
    	steps{
    	  container('build-agent')
	    git 'https://github.com/careem111/helloworld1_private.git'
	    sh 'mvn clean install package'
	    sh 'sudo -i;cp webapps/target/*.war /root/images'
	    sh 'docker build'
        	}
            }
        } 
    }
