pipeline{
    agent none
    stages{
      stage('Create agent'){
	    agent {
		kubernetes {
		    label "build-pod"
		    cloud "kubernetes"
		    yaml '''
	apiVersion: v1
	kind: Pod
	metadata:
	  name: build
	  label: build
	  namespace: default
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
    steps{
                    git 'https://github.com/careem111/helloworld1_private.git'
                    sh 'mvn clean install package'
                    sh 'sudo -i;cp webapps/target/*.war /root/images'
                    sh 'docker build'

        	}
            }
        } 
    }
